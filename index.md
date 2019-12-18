## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/sorebear/sorebear.github.io/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Blocks

### Adding Block Type Template
There is not a default template for a Block Type. This preprocess will add one.

```php
function THEME_theme_suggestions_block_alter(&$suggestions, &$vars) {

}
```

# Theme Settings

### Add Settings From to Theme

```php
use Drupal\Core\Form\FormStateInterface;

function THEME_form_system_theme_settings_alter(&$form, FormStateInterface &$form_state, $form_id = NULL) {
  if (isset($form_id)) {
    return;
  }
  
  $form['theme_settings'] = array(
    '#type' => 'fieldset',
    '#title' => t('Theme Settings'),
    '#weight' => -20,
  );

  $form['theme_settings']['field_1'] = array(
    '#type' => 'textfield',
    '#title' => t('Field 2 of Theme Settings'),
    '#default_value' => theme_get_setting('field_1'),
  );

  $form['theme_settings']['field_2'] = array(
    '#type' => 'checkbox',
    '#title' => t('Field 2'),
    '#description' => t('Field 2 is dependent on Field 1 having a value'),
    '#default_value' => theme_get_setting('field_2'),
    '#states' => [
      'visible' => [
        ':input[name="field_1"]' => ['filled' => TRUE]
      ]
    ]
  );
  
  $form['theme_settings']['field_3'] = array(
    '#type' => 'checkbox',
    '#title' => t('Field 3'),
    '#description' => t('Field 3 is dependent on Field 2 being checked'),
    '#default_value' => theme_get_setting('field_3'),
    '#states' => [
      'visible' => [
        ':input[name="field_2"]' => ['checked' => TRUE]
      ]
    ]
  );
}
