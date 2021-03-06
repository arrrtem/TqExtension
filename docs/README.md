# Writing the tests

- The files for testing (images, documents, videos etc.) should be stored in [resources](/behat/resources) folder.
- To see all, available in your system, steps execute the `bin/behat -dl`.
- Some examples can be found [here](examples).

## Table of contents

- [TqContext](#tqcontext)
- [DrushContext](#drushcontext)
- [EmailContext](#emailcontext)
- [FormContext](#formcontext)
- [RedirectContext](#redirectcontext)
- [UserContext](#usercontext)
- [WysiwygContext](#wysiwygcontext)

### TqContext

```gherkin
Given I switch to opened window
```

```gherkin
Given I switch back to main window
```

```gherkin
Given I switch to CKFinder window
```

```gherkin
Given I switch to an iframe "mediaBrowser"
```

```gherkin
When I switch back from an iframe
```

```gherkin
Given I should use the "1280x800" screen resolution
```

```gherkin
## In role of element selector can be:
## - CSS selector;
## - Inaccurate text;
## - Region name from "behat.yml";
When I (press|click|double click|right click) on ".link"
```

```gherkin
## This method must be used instead of 'I wait for AJAX to finish'!
Then I wait until AJAX is finished
```

```gherkin
## Region can be found by CSS selector or name from "region_map" parameter of "behat.yml".
Then I work with elements in "header" region
```

```gherkin
## That step helps to exit from element visibility scope that was defined by
## executing of previous step.
Then I checkout to whole page
```

```gherkin
Then I wait 60 seconds
```

```gherkin
## In selector role can be: inaccurate text or label, CSS or region name.
And scroll to "Meta tags" element
```

### DrushContext

```gherkin
Given I login with one time link( (1))
Then drush uli( admin)
```

### [EmailContext](examples/EMAIL.md)

```gherkin
## At least one field should be specified.
Then I check that email for "test@ffwagency.com" contains:
  | subject | New email letter   |
  | body    | The body of letter |
```

```gherkin
Then I click on link "Test" in email( that was sent on "test@ffwagency.com")
```

```gherkin
Then I check that email for "test@ffwagency.com" was sent
```

```gherkin
## To use this step you should correctly configure your Behat.
Then I login with credentials that was sent on "test@ffwagency.com"
```

### FormContext

```gherkin
Given I typed "Joe" in the "name" field and choose 2 option from autocomplete variants
```

```gherkin
## - The selector of form field can be inaccurate label, ID or name of the HTML element.
## - The selector of user entity field can be machine name or label of the field.
Then I fill in "field_company[und][0]" with value of field "user_company" of current user
```

```gherkin
Given I (un)check the boxes:
  | Consumer Products  |
  | ICT                |
  | Financial Services |
```

```gherkin
## - The button can be found by ID, name, label or CSS selector.
## - The label of radio button can be specified inaccurately.
## - If element has more than one label and one of them is hidden, then
##   will used only visible, if exist.
## - If trying to get the field by label, then it must have the "for" attribute
##   and element with ID, specified in that attribute, must exist.
## - The @javascript tag is necessary when "customized" is used!
Given I check the( customized) "Show" radio button
```

```gherkin
## This method must be used instead of 'I fill in "field" with "value"'!
## Drupal tokens available.
Then I fill "last_name" with "Bondarenko"
```

```gherkin
## This method must be used instead of 'I fill in the following:'!
Then I fill the following:
  | first_name | Sergey    |
  | last_name | Bondarenko |
```

```gherkin
And attach file "600x400.jpg" to "Logotype"
```

```gherkin
## - This method works with "Clientside Simple Hierarchical Select",
##   "Simple Hierarchical Select" and "Hierarchical Select" modules.
## - The label of field or wrapper ID can be used as selector.
Then I select the following in "Categories" hierarchical select:
  | EN                  |
  | Financial Services  |
```

```gherkin
Then should see the thumbnail
```

```gherkin
And should see no errors
```

```gherkin
And pick "Kiyv" from "City"
```

```gherkin
Then I choose "October 13, 2017" in "Date" datepicker
```

```gherkin
Then I check that "Date" datepicker contains "October 13, 2017" date
```

```gherkin
Then I check that "October 13, 2017" is available for "Date" datepicker$
```

### RedirectContext

```gherkin
## Waits for only one redirect and goes to the next step.
Then I should be redirected
```

```gherkin
## Waits as long as URL of the page will not be the same as specified.
## - The URL can be relative or absolute.
## - By default, the waiting timeout is set to 30 seconds, but you can change
##   this in "behat.yml".
Then I should be redirected on "https://example.com"
```

```gherkin
And user should( not) have an access to the following pages:
  | admin/people/create |
  | node/add/article    |
  | user/1/edit         |
```

```gherkin
## This step should be used instead of "I am at" if page should be checked for accessibility
## before visiting.
And I am on the "admin/config" page( and HTTP code is "200")
## Also, an alias can be used:
And (I )visit the "admin/config" page( and HTTP code is "200")
```

### UserContext

```gherkin
## - This method must be used instead of 'I am logged in as a user with the "administrator" role'!
## - Multiple roles can be listed by comma: 'And logged in as a user with "administrator, editor" roles'.
Given I am logged in as a user with "administrator" role
```

```gherkin
## - Taxonomy Term Reference supported. You must specify name of term and
##   correct value will be saved.
## - The machine name or label of a field can be used as selector.
Given I am logged in as a user with "administrator" role and filled fields:
  | Full name | Sergey Bondarenko   |
  | Position  | Web Developer       |
  | Company   | FFW                 |
```

```gherkin
## Fill login form with existing credentials.
Then I am logged in with credentials:
  | username | BR0kEN |
  | password | p4sswd |
```

```gherkin
## This step must be used instead of "I am an anonymous user" because it has more
## strict checking for authenticated user.
Given I am unauthorized user
```

### [WysiwygContext](examples/WYSIWYG.md)

```gherkin
## If this step was used, then you no need to specify selector for next steps
## from this context while working with only one editor.
Given I work with "Presentation" WYSIWYG editor
```

```gherkin
Then I fill "<strong>Text</strong>" in "Presentation" WYSIWYG editor
```

```gherkin
Then I type "additional text" in "Presentation" WYSIWYG editor
```

```gherkin
Then I should see "Text" in "Presentation" WYSIWYG editor
```

```gherkin
Then I should not see "vulnerability" in "Presentation" WYSIWYG editor
```

```gherkin
Then I fill in following WYSIWYG editors
  | Editor locator | Value |
```
