# Hyvä UI - modal.A - simple

[![License]](../../../LICENSE.md)
[![Hyva Supported Versions]](https://docs.hyva.io/hyva-ui-library/getting-started.html)
[![Tailwind Supported Versions]](https://tailwindcss.com/)
[![AlpineJS Supported Versions]](https://alpinejs.dev/)
[![Figma]](https://www.figma.com/@hyva)

These examples are just a button which triggers a modal. You can use this as a starting point for your own needs.

There are different ways to use modals within Hyvä. 
See our [documentation](https://docs.hyva.io/hyva-themes/view-utilities/modal-dialogs/index.html) for more info.

## Usage - Template

1. Ensure you've installed [x-collapse] in your project (see [Requirements](#requirements) below)
2. Copy or merge the following files/folders into your theme:
   * `Magento_Theme/templates`
   * `Magento_Theme/layout`
3. Adjust the content and code to fit your own needs and save
4. Create your development or production bundle by running `npm run watch` or `npm run build-prod` in your
   theme's tailwind directory

### With or without the view model

The file `modal-php.phtml` contains a modal with the use of the PHP ViewModel. You can always override the default
container template with `->withContainerTemplate('My_Module::modal-container.phtml')` or use a content template with 
`->withTemplate('My_Module::dialog-content.phtml')` to make your code more readable or less repetitive.

The file `modal-js.phtml` contains a JS-only solution, more suitable for CMS content. 

### Confirmation modal

The confirmation modal is a variant of the modal.
See the [documentation](https://docs.hyva.io/hyva-themes/view-utilities/modal-dialogs/confirmation-dialogs.html)
for more info. The file `confirmation-php.phtml` contains an example using the PHP ViewModel.
In this case the content template is overridden with the file confirmation-content-template.phtml. 
Be sure to change the `withTemplate()` function to reference the correct file.  

Similar to `modal-js.phtml`, the confirmation modal can also be used in JS-only. 
See the same documentation for examples.

## Preview

| Desktop      | Mobile       |
| ------------ | ------------ |
| ![preview-1] | ![preview-2] |

[preview-1]: ./media/A-simple.jpg "Preview of Modal in action on Desktop view"
[preview-2]: ./media/A-simple-mobile.jpg "Preview of Modal in action on Mobile view"

## Notes

The font-family is not altered, unlike the font-sizes and colors. You can change those to fit your design.

## License

Hyvä Themes - https://hyva.io

Copyright © Hyvä Themes B.V 2020-present. All rights reserved.

This product is licensed per Magento install. Please see the LICENSE.md file in the root of this repository for more
information.

[License]: https://img.shields.io/badge/License-004d32?style=for-the-badge "Link to Hyvä License"
[Figma]: https://img.shields.io/badge/Figma-gray?style=for-the-badge&logo=Figma "Link to Figma"

[Hyva Supported Versions]: https://img.shields.io/badge/Hyv%C3%A4-1.2,_1.3-0A23B9?style=for-the-badge&labelColor=0A144B "Hyvä Supported Versions"
[Tailwind Supported Versions]: https://img.shields.io/badge/Tailwind-2,_3-06B6D4?style=for-the-badge&logo=TailwindCSS "Tailwind Supported Versions"
[AlpineJS Supported Versions]: https://img.shields.io/badge/AlpineJS-3-8BC0D0?style=for-the-badge&logo=alpine.js "AlpineJS Supported Versions"
