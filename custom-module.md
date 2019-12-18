# Custom Modules

For all of these examples, we will assume the module we are creating is named 'sorebear_module'.

## Module with Settings Form, CSS, and JavaScript

### File Structure

```
- css/
  - sorebear-module.css
- js/
  - sorebear-module.js
- src/
  - Form/
    - SoreBearModuleSettingsForm.php
- sorebear_module.info.yml
- sorebear_module.libraries.yml
- sorebear_module.links.menu.yml
- sorebear_module.module
- sorebear_module.permissions.yml
- sorebear_module.routing.yml
```

#### sorebear_module.info.yml
```yml
name: Sore Bear Module
type: module
description: A module with a settings form, CSS, and JavaScript.
package: Sore Bear Custom
core: 8.x
configure: sorebear_module.settings
dependencies:
  - drupal:views
```

#### sorebear_module.info.yml
```yml
assets:
  version: 1.x
  css:
    theme:
      css/sorebear-module.css: {}
  js:
    js/sorebear-module.js: {}
```

#### sorebear_module.links.menu.yml
```yml
sorebear_module.settings:
  title: Sore Bear Module Settings
  description: Change the settings to the module.
  # Places link under 'Configuration > User Interface'
  parent: system.admin_config_ui
    # For 'Configuration > Development' use: system.admin_config_development
  route_name: sorebear_module.settings
```

#### sorebear_module.permissions.yml
```yml
administer sorebear module:
  title: Sore Bear Module
  description: Administer the module settings.
  retrict access: TRUE
```

#### sorebear_module.settings
This code in the 'parent: ' line places the link under 'Config > User Interace'.
To place the link under 'Config > Development', use: `parent: system.admin_config_development`
```yml
sorebear_module.settings:
  # Places link under 'Configuration > User Interface'
  path: '/admin/config/user-interface/sorebear-module'
    # For 'Configuration > Development' use: 'admin/config/development/sorebear-module'
  defaults:
    _title: 'Sore Bear Module Settings'
    _form: '\Drupal\sorebear_module\Form\SoreBearModuleSettingsForm'
  requirements:
    _permission: 'administer sorebear module'
```

