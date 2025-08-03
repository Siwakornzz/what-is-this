# i18n Implementation Protocol

## Overview
This document outlines the internationalization (i18n) implementation strategy for policy translations and multilingual support in the admin frontend application.

## Architecture Decision

### Chosen Approach: Frontend-Based i18n with react-i18next
- **Backend sends**: Simple policy keys (path + method)
- **Frontend handles**: All translation logic and language switching
- **Benefits**: Better performance, instant language switching, scalable for multiple languages

### Alternative Approaches Considered
1. **Backend-driven translations**: Rejected due to performance overhead and complexity
2. **Hybrid approach**: Unnecessary complexity for current requirements

## File Structure

```
src/i18n/
├── index.ts                    # Main i18n configuration
├── translations/
│   ├── th/                    # Thai translations
│   │   ├── index.ts          # Export all Thai modules
│   │   ├── admin.json        # Admin service translations
│   │   ├── roles.json        # Role service translations
│   │   ├── building.json     # Building service translations
│   │   ├── bills.json        # Bills service translations
│   │   ├── maintenance.json  # Maintenance service translations
│   │   ├── auth.json         # Authentication translations
│   │   └── common.json       # Common UI translations
│   └── en/                   # English translations
│       ├── index.ts          # Export all English modules
│       └── [same structure as th/]
```

## Translation File Format

Each service translation file follows this structure:

```json
{
  "policies": {
    "actionname": "Translated Action Name"
  },
  "descriptions": {
    "actionname": "Detailed description of the permission"
  },
  "groupName": "Service Group Display Name",
  "groupDescription": "Description of what this service group manages"
}
```

### Example: admin.json
```json
{
  "policies": {
    "createuser": "สร้างผู้ใช้งานใหม่",
    "deleteuser": "ลบผู้ใช้งาน",
    "rolepermissionsmatrix": "จัดการสิทธิ์บทบาท"
  },
  "descriptions": {
    "createuser": "สิทธิ์ในการสร้างบัญชีผู้ใช้งานใหม่ในระบบ",
    "deleteuser": "สิทธิ์ในการลบบัญชีผู้ใช้งานออกจากระบบ"
  },
  "groupName": "จัดการผู้ดูแลระบบ",
  "groupDescription": "จัดการข้อมูลผู้ดูแลระบบและผู้ใช้งาน"
}
```

## Usage Pattern

### Hook-based Translation
```typescript
import { usePolicyTranslation } from '../utils/policyTranslations';

const { getPolicyName, getPolicyDescription, getGroupName } = usePolicyTranslation();

// Translate policy from API path
const policyName = getPolicyName('admin/createuser'); // "สร้างผู้ใช้งานใหม่"
const description = getPolicyDescription('admin/createuser'); // "สิทธิ์ในการสร้าง..."
const groupName = getGroupName('admin'); // "จัดการผู้ดูแลระบบ"
```

### Key Generation Logic
- API path: `admin/createuser` 
- Translation key: `admin.policies.createuser`
- Description key: `admin.descriptions.createuser`
- Group name key: `admin.groupName`

## Implementation Benefits

### 1. Performance Optimized
- Translations cached in frontend
- No API calls for language switching
- Instant UI language changes

### 2. Developer Experience
- Modular translation files by service
- Type-safe translation keys
- Fallback mechanisms for missing translations

### 3. Scalability
- Easy to add new languages (create new folder)
- Service-based organization prevents merge conflicts
- Clear separation of concerns

### 4. Maintainability
- Each service team can manage their own translations
- Consistent structure across all services
- Automated fallbacks for missing keys

## Integration Points

### 1. Backend API Response
Backend continues to send simple policy structure:
```json
{
  "path": "admin/createuser",
  "method": "post"
}
```

### 2. Frontend Processing
Frontend transforms this into translated display:
```typescript
// From API: { path: "admin/createuser", method: "post" }
// Becomes: { 
//   name: "สร้างผู้ใช้งานใหม่", 
//   description: "สิทธิ์ในการสร้างบัญชีผู้ใช้งานใหม่ในระบบ" 
// }
```

---

## Backend-Driven Translation Key Management Protocol

This section outlines the crucial collaboration protocol for managing translation keys, especially for dynamic content like policies, where the backend is the single source of truth for the keys themselves.

### Principle: Backend Generates Key Templates

The backend is responsible for defining and providing the complete set of translation keys. This ensures consistency and prevents discrepancies between backend logic and frontend translations.

### Backend Responsibilities:

1.  **Key Definition:** All `groupKey` and `policyKey` identifiers are defined and managed within the backend.
2.  **Template Generation Script:** The backend repository **must** include a script (e.g., `npm run generate-i18n-keys`, `php artisan app:generate-translation-keys`) that automatically generates a JSON file containing the complete structure of all translation keys.
    *   **Generated File Name:** `i18n_keys.template.json` (or `policy_keys.template.json` for specific domains)
    *   **Location:** This generated file should be committed to the **frontend repository** (e.g., in `src/i18n/templates/` or `template/`) whenever there is an update to the keys (e.g., new policies, new groups).
    *   **Content:** The template file will contain the full hierarchy of keys with empty string values, serving as a blueprint for frontend translations.

    ```json
    // Example: src/i18n/templates/policy_keys.template.json
    {
      "groups": {
        "auth": {
          "name": "",
          "description": ""
        },
        "admin_management": {
          "name": "",
          "description": ""
        }
      },
      "items": {
        "auth.login": {
          "name": "",
          "description": ""
        },
        "admin.create": {
          "name": "",
          "description": ""
        }
      }
    }
    ```

### Frontend Responsibilities:

1.  **Pull Latest Template:** Frontend developers must regularly pull the latest `i18n_keys.template.json` (or domain-specific templates) from the repository.
2.  **Update Translation Files:** Use the generated template to update the actual language-specific translation files (e.g., `th/policies.json`, `en/policies.json`).
    *   **Comparison Tools:** Leverage file comparison tools (diff tools) to easily identify new or changed keys in the template.
    *   **Translation:** Fill in the empty `""` values in the language-specific JSON files with the appropriate translated text.
3.  **No Manual Key Creation:** Frontend developers should **never** manually create new translation keys for backend-driven content. All such keys must originate from the backend-generated template.

### Benefits of this Protocol:

*   **Single Source of Truth for Keys:** The backend is the definitive source for all translation keys, eliminating discrepancies.
*   **Reduced Errors:** Minimizes typos and missing keys in frontend translation files.
*   **Streamlined Workflow:** Provides a clear, automated process for synchronizing key structures between teams.
*   **Improved Maintainability:** Changes to keys are propagated efficiently, and translation efforts are focused on filling in values, not guessing keys.
*   **Scalability:** Easily supports a large number of keys and multiple languages without complex manual coordination.

---

## Future Extensibility

### Adding New Languages
1. Create new language folder: `src/i18n/translations/ja/`
2. Copy structure from existing language
3. Translate content
4. Update language selector component

### Adding New Services
1. Create service translation file: `[service].json`
2. Add to index.ts exports
3. Follow established JSON structure
4. Translation keys automatically work with existing hook

## Configuration

### Default Language: Thai (th)
### Supported Languages: Thai (th), English (en)
### Fallback Language: English (en)

## Quality Assurance

### Translation Standards
- Consistent terminology across services
- Clear, concise descriptions
- Professional tone appropriate for admin interface
- Contextually appropriate translations

### Testing Strategy
- Unit tests for translation hook functionality
- Integration tests for language switching
- Visual regression tests for different languages
- Performance tests for translation loading

## Best Practices

### For Developers
1. Always use the `usePolicyTranslation` hook
2. Provide meaningful fallbacks
3. Test with multiple languages
4. Keep translation keys descriptive

### For Translators
1. Maintain consistency in terminology
2. Consider context when translating
3. Keep translations concise for UI space
4. Follow established patterns in existing translations

This implementation provides a robust, scalable foundation for multilingual support while maintaining optimal performance and developer experience.