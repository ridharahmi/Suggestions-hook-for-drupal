# Custom suggestions hook for drupal

### Suggestions form
```
/**
 * @param array $suggestions
 * @param array $variables
 * @param $hook
 * suggestions form
 */
function suggestions_theme_suggestions_form_alter(array &$suggestions, array &$variables, $hook)
{
    if (isset($variables['element']['#id'])) {
        $form_id = str_replace('-', '_', $variables['element']['#id']);
        $suggestions[] = $hook . '__' . $form_id;
    }
}
```
### Suggestions field details
```
/**
 * @param array $suggestions
 * @param array $variables
 * @param $hook
 * suggestions field details
 */
function suggestions_theme_suggestions_details_alter(array &$suggestions, array &$variables, $hook)
{
    if (isset($variables['element']['#id'])) {
        $id = str_replace("-", "_", $variables['element']['#id']);
        $suggestions[] = $hook . '__' . $id;
    }
}
```
### Suggestions field input
```
/**
 * @param array $suggestions
 * @param array $variables
 * @param $hook
 * suggestions field input
 */
function suggestions_theme_suggestions_input_alter(array &$suggestions, array $variables, $hook)
{
    if (isset($variables['element']['#id'])) {
        $id = str_replace("-", "_", $variables['element']['#id']);
        $suggestions[] = $hook . '__' . $id;
    }
}
```
### Suggestions field table
```
/**
 * @param array $suggestions
 * @param array $variables
 * @param $hook
 * suggestions field table
 */
function suggestions_theme_suggestions_table_alter(array &$suggestions, array &$variables, $hook)
{
    if (isset($variables['attributes']['id'])) {
        $table_id = $variables['attributes']['id'];
        $id = str_replace("-", "_", $table_id);
        $suggestions[] = $hook . '__' . $id;
    }
}
```
### Suggestions field file managed
```
/**
 * @param array $suggestions
 * @param array $variables
 * @param $hook
 * suggestions field file managed
 */
function suggestions_theme_suggestions_file_managed_file_alter(array &$suggestions, array $variables, $hook)
{
    if (isset($variables['element']['#id'])) {
        $id = str_replace("-", "_", $variables['element']['#id']);
        $suggestions[] = $hook . '__' . $id;
    }

}
```
### Suggestions form element
```
/**
 * @param array $suggestions
 * @param array $variables
 * @param $hook
 * suggestions form element
 */
function suggestions_theme_suggestions_form_element_alter(array &$suggestions, array $variables, $hook)
{
    $elementId = str_replace('-', '_', $variables['element']['#id']);
    $suggestions[] = $hook . '__' . $elementId;
}
```
### Suggestions container
```
/**
 * @param array $suggestions
 * @param array $variables
 * @param $hook
 * suggestions container
 */
function suggestions_theme_suggestions_container_alter(array &$suggestions, array $variables, $hook)
{
    $pieces = [
        $variables['element']['#type'],
    ];
    $suggestions[] = $hook . implode('_', $pieces);
}
```
### Suggestions form element label
```
/**
 * @param array $suggestions
 * @param array $variables
 * @param $hook
 * suggestions form element label
 */
function suggestions_theme_suggestions_form_element_label_alter(array &$suggestions, array $variables, $hook)
{
    if (isset($variables['element']['#id'])) {
        $id = $variables['element']['#id'];
        $suggestions[] = $hook . '__' . $id;
    }
}
```
### Suggestions fieldset
```
/**
 * @param array $suggestions
 * @param array $variables
 * @param $hook
 * suggestions fieldset
 */
function suggestions_theme_suggestions_fieldset_alter(array &$suggestions, array $variables, $hook)
{
    if (isset($variables['element']['#id'])) {
        $id = $variables['element']['#id'];
        $suggestions[] = $hook . '__' . $id;
    }
}
```
### Suggestions field checkboxes
```
/**
 * @param array $suggestions
 * @param array $variables
 * @param $hook
 * suggestions checkboxes
 */
function suggestions_theme_suggestions_checkboxes_alter(array &$suggestions, array $variables, $hook)
{
    if (isset($variables['element']['#id'])) {
        $id = $variables['element']['#id'];
        $suggestions[] = $hook . '__' . $id;
    }
}
```
### Suggestions pager view
```
/**
 * @param array $suggestions
 * @param array $variables
 * @param $hook
 * suggestions pager
 */
function suggestions_theme_suggestions_pager_alter(array &$suggestions, array $variables, $hook)
{
    $current_path = \Drupal::service('path.current')->getPath();
    $result = \Drupal::service('path.alias_manager')->getAliasByPath($current_path);

    $path_alias = trim($result, '/');
    $path_alias = str_replace('/', '-', $path_alias);
    $path_alias = str_replace('-', '_', $path_alias);

    $suggestions[] = $hook . '__' . $path_alias;
}
```
### Suggestions block
```
/**
 * Implements hook_theme_suggestions_HOOK_alter() for form templates.
 * @param array $suggestions
 * @param array $variables
 */
function suggestions_theme_suggestions_block_alter(array &$suggestions, array $variables)
{
    // Block suggestions for custom block bundles.
    if (isset($variables['elements']['content']['#block_content'])) {
        array_splice($suggestions, 1, 0, 'block__bundle__'
            . $variables['elements']['content']['#block_content']
                ->bundle());
    }
}
```
### Suggestions view exposed form
```
/**
 * Implements hook_theme_suggestions_HOOK_alter().
 */
function suggestions_theme_suggestions_views_exposed_form_alter(array &$suggestions, array $variables)
{
    $suggestions[] = 'views_exposed_form__' . str_replace(
            ['views-exposed-form-', '-'],
            ['', '_'],
            $variables['form']['#id']);
}
```
### Suggestions view
```
/**
 * @param array $suggestions
 * @param array $variables
 * @param $hook
 * suggestions view
 */
function suggestions_theme_suggestions_views_view_alter(array &$suggestions, array &$variables, $hook)
{
    if ($variables['view']->id() && $variables['view']->current_display) {
        $suggestions[] = $hook . '__' . $variables['view']->id() . '__' . $variables['view']->current_display;
    }
}
```
### Suggestions view unformatted
```
/**
 * @param array $suggestions
 * @param array $variables
 * @param $hook
 * suggestions view unformatted
 */
function suggestions_theme_suggestions_views_view_unformatted_alter(array &$suggestions, array &$variables, $hook)
{
    if ($variables['view']->id() && $variables['view']->current_display) {
        $suggestions[] = $hook . '__' . $variables['view']->id() . '__' . $variables['view']->current_display;
    }
}
```

### Suggestions field radios
```
/**
 * @param array $suggestions
 * @param array $variables
 * @param $hook
 */
function suggestions_theme_suggestions_radios_alter(array &$suggestions, array $variables, $hook)
{
    if (isset($variables['element']['#id'])) {
        $id = str_replace("-", "_", $variables['element']['#id']);
        $suggestions[] = $hook . '__' . $id;
    }
}
```
### Suggestions field select
```
/**
 * @param array $suggestions
 * @param array $variables
 * @param $hook
 */
function suggestions_theme_suggestions_select_alter(array &$suggestions, array $variables, $hook)
{
    if (isset($variables['element']['#id'])) {
        $id = str_replace("-", "_", $variables['element']['#id']);
        $suggestions[] = $hook . '__' . $id;
    }
}
```

### Suggestions Suggestions
```
/**
 * @param array $suggestions
 * @param array $variables
 * @param $hook
 */
function suggestions_theme_suggestions_paragraph_alter(array &$suggestions, array &$variables, $hook)
{
    $paragraph = $variables['elements']['#paragraph'];
    $node = \Drupal::routeMatch()->getParameter('node');
    if (!empty($node)) {
        $suggestions[] = $hook . '__' . $paragraph->bundle() . '__' . $node->getType() . '__' . $node->id();
    }
}
```