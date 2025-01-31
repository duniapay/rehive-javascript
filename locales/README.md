# Rehive app translations

The rehive app uses i18n standard json language files along with i18next to manage translations in the app. These language files are divided into the following different namespaces:

- Common
- Accounts
- Auth
- Onboarding
- PoS
- Products
- Profile
- Rewards
- Settings

## Language files

### Variables

Variables can be included in the strings using `{{variable_name}}`. The list of available variables in each namespace will be added soon.

### Formatting

(Not yet implemented, but this is the intended usage)

The following formatting identifiers are available:

- `**text**` for Bold

## Usage

These base translations are hard coded on the app. However each one of these can be overwritten ~~using the locales section of the app service in the dashboard (forthcoming) or~~ using the [App service directly](#app-service)..

### Config

Above the fixed content in the app, there is also client generated app content such as home screen prompts/alerts, group names/descriptions, fee names, etc. These can also be localized by providing a key as the text/label field in the dashboard and then adding the related translations to the app service.

### Localize

To be added

## App service

Currently translations have to be added through the wallet service API/swagger (while the dashboard UI for managing locales is being completed). This can be accessed at https://wallet.services.rehive.io/swagger/ (base URL: wallet.services.rehive.io/api). Note: remember to authorize by adding `Token <admin_token>` by click the green Authorize button top right of the screen.

### Adding a new translation

This is done by making a new POST request to `/admin/locales/` with the following information:

```json
{
  "id": "string",
  "translation": {},
  "name": "string"
}
```

where `id` is the language code (i.e. `en-US`), `name` is the language name (English (US)) and `translation` is a nested json object of each locale file for example:

```json
{
  "translation": {
    "accounts": { ... },
    "auth": { ... },
    "common": { ... },
    ...
  },
}
```

### Updating translations

This is done by making a PUT/PATCH request to `/admin/locales/{locales_id}/` where `locales_id` is the `id` / language code used above (i.e. `en-US`). When updating the locales please ensure to include the entire new translations object.
