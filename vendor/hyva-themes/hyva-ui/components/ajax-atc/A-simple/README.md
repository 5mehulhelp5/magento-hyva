# Hyvä UI - ajax-atc.A - simple

[![License]](../../../LICENSE.md)
[![Hyva Supported Versions]](https://docs.hyva.io/hyva-ui-library/getting-started.html)
[![Tailwind Supported Versions]](https://tailwindcss.com/)
[![AlpineJS Supported Versions]](https://alpinejs.dev/)
[![Figma]](https://www.figma.com/@hyva)

Streamline your shopping experience with our Ajax Add To Cart UI Component.

Seamlessly add products to your cart without page reloads, and see a quick modal confirming your selection.

## Usage - Template

1. Copy or merge the following files/folders into your theme:
   * `Magento_Theme/templates`
   * `Magento_Theme/layout`
2. Adjust the content and code to fit your own needs and save
3. Create your development or production bundle by running `npm run watch` or `npm run build-prod` in your
   theme's tailwind directory

### Configuration Options

This UI component offers customization options without modifying the corresponding phtml files.

To configure this UI component,
utilize the provided options as outlined in the `src/Magento_Theme/layout/default.xml` file.

| Option Name          | Type    | Available Values           | Default                                            | Description                                                 |
| -------------------- | ------- | -------------------------- | -------------------------------------------------- | ----------------------------------------------------------- |
| `delay`              | number  | _Number Range_             | 500                                                | Extra delay in milliseconds added to the loader             |
| `show_sku`           | boolean | true, false                | true                                               | Enable to sku in product options                            |
| `display_on_success` | string  | `modal`, `minicart`, false | `modal`                                            | What to show on success                                     |
| `form_selectors`     | string  |                            | `#product_addtocart_form, .product_addtocart_form` | Configure the form selectors that will trigger the Ajax ATC |

## Preview

| Type  | Desktop      | Tablet       | Mobile       |
| ----- | ------------ | ------------ | ------------ |
| Modal | ![preview-1] | ![preview-2] | ![preview-3] |

[preview-1]: ./media/A-simple.jpg "Preview of the Modal on Desktop view"
[preview-2]: ./media/A-simple-tablet.jpg "Preview of the Modal on Tablet view"
[preview-3]: ./media/A-simple-mobile.jpg "Preview of the Modal on Mobile view"

> The `false` and `minicart` use Hyvä Default Theme for the style

## Notes

The font-family is not altered, unlike the font-sizes and colors. You can change those to fit your design.

For the best experience, set a Default Timeout for the Success Message in `Stores → Configuration → Hyvä Themes → General → Success Message Default Timeout` to a specific value.

The Modal option will fallback to the false option for Grouped and Bundled Products, and will just show the default message.

### Using Ajax with Synchronize widget products with backend storage

AJAX-based UI components, including this one, are incompatible with the Magento 2 setting `Synchronize widget products with backend storage`.

To ensure proper functionality, please disable this setting before using this UI component.

The setting can be found in `Stores → Configuration → Catalog → Catalog`.

## License

Hyvä Themes - https://hyva.io

Copyright © Hyvä Themes B.V 2020-present. All rights reserved.

This product is licensed per Magento install. Please see the LICENSE.md file in the root of this repository for more
information.

[License]: https://img.shields.io/badge/License-004d32?style=for-the-badge "Link to Hyvä License"
[Figma]: https://img.shields.io/badge/Figma-gray?style=for-the-badge&logo=Figma "Link to Figma"

[Hyva Supported Versions]: https://img.shields.io/badge/Hyv%C3%A4-1.2,_1.3-0A23B9?style=for-the-badge&labelColor=0A144B "Hyvä Supported Versions"
[Tailwind Supported Versions]: https://img.shields.io/badge/Tailwind-3-06B6D4?style=for-the-badge&logo=TailwindCSS "Tailwind Supported Versions"
[AlpineJS Supported Versions]: https://img.shields.io/badge/AlpineJS-3-8BC0D0?style=for-the-badge&logo=alpine.js "AlpineJS Supported Versions"
