# Modules

The following are references for building Custom Modules. The module machine name should be only lowercase letters and underscores. Custom modules should be places inside of your file structure at `/modules/custom`. For all the following examples, we will imagine we're creating a module called `bear_hug`.

## Basic File Structure

Create a folder called `bear_hug`, so your module will live at `/modules/custom/bear_hug`. Inside that folder we will create the following files:

## bear_hug.info.yml

```yml
name: Bear Hug
core: 8.x
type: module
description: This is a sample module named 'Bear Hug'
package: Sorebear Custom
dependencies:
  - drupal:views
```
