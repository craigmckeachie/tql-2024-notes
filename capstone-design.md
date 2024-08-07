# Capstone Design

- [PRS Design Screenshots](https://www.figma.com/design/w0r81D2ouvnMd247ebKwyz/Purchase-Request-System?node-id=0-1&t=M8aGgbORODyzwobV-1)

## Assignment

1. Create home page (including common layout)
2. Create list page (vendors)
3. Create a form page (vendor create/edit)
   - Vertical straight down page

## Scope

- Dropdown menus are a stretch goal (where you see three vertical dots)
- Left Navigation `+ Create New Button` is a stretch goal
  - remove it or leave it non-functional
- Any icon is a stretch goal
- To replace icons and dropdown menus
  - Use links or buttons depending on situation
- Any HTML Form can be displayed in one column vertically, no need to do do multiple column layouts
  - Multiple column layouts are a stretch goal

## Style Guide

- Grey Background
  ```
  class="bg-body-tertiary"
  ```
- Left Navigation Icons:

  ```html
  <svg class="bi pe-none me-2" width="16" height="16" fill="#FFFFFF">
    <use xlink:href="./images/bootstrap-icons.svg#cart"></use>
  </svg>

  <svg class="bi pe-none me-2" width="16" height="16" fill="#FFFFFF">
    <use xlink:href="./images/bootstrap-icons.svg#grid"></use>
  </svg>

  <svg class="bi pe-none me-2" width="16" height="16" fill="#FFFFFF">
    <use xlink:href="./images/bootstrap-icons.svg#building"></use>
  </svg>

  <svg class="bi pe-none me-2" width="16" height="16" fill="#FFFFFF">
    <use xlink:href="./images/bootstrap-icons.svg#people"></use>
  </svg>
  ```

- Buttons
  - blue
    ```
    class="btn btn-primary"
    ```
  - white with blue outline
    ```
    class="btn btn-outline-primary
    ```
