# Hyvä UI - slider.A - basic

[![License]](../../../LICENSE.md)
[![Hyva Supported Versions]](https://docs.hyva.io/hyva-ui-library/getting-started.html)
[![Tailwind Supported Versions]](https://tailwindcss.com/)
[![AlpineJS Supported Versions]](https://alpinejs.dev/)
[![Figma]](https://www.figma.com/@hyva)

This component uses custom templates for the 
[generic slider template](https://docs.hyva.io/hyva-themes/view-utilities/custom-sliders.html) that comes with Hyvä.

## Usage - Template

1. Copy or merge the following files/folders into your theme:
   * `Magento_Theme/templates`
2. Replace the example `$items` with your own collection of slide data
3. Adjust the content and code to fit your own needs and save
4. Create your development or production bundle by running `npm run watch` or `npm run build-prod` in your
   theme's tailwind directory

> There's an example how to insert the `slider-a.phtml` into your homepage in `Magento_Theme/layout/cms_index_index.xml`

### Configuration Options

This UI component offers customization options without modifying the corresponding phtml files.

To configure this UI component,
utilize the provided options as outlined in the `src/Magento_Theme/layout/cms_index_index.xml` file.

| Option Name        | Type            | Available Values            | Default | Description                                                                 |
| ------------------ | --------------- | --------------------------- | ------- | --------------------------------------------------------------------------- |
| `show_arrows`      | boolean, string | true, false, `start`, `end` | `end`   | Controls whether the navigation arrow should be shown and on which position |
| `show_dots`        | boolean         | true, false                 | true    | Controls whether the navigation dots should be shown                        |
| `load_first_eager` | boolean         | true, false                 | false   | If to show the first image, iframe, or more, as eager                       |

> Normally it's not recommended to use sliders above the fold; but if you want, make sure to set the `load_first_eager` to true

## Preview

| Type    | Desktop      | Mobile       |
| ------- | ------------ | ------------ |
| Default | ![preview-1] | ![preview-2] |

[preview-1]: ./media/A-basic.jpg "Preview of Slider in Desktop View"
[preview-2]: ./media/A-basic-mobile.jpg "Preview of Slider in Mobile View"

## Notes

There is no container around this element, assuming your theme already has some kind of container.

The font-family is not altered, unlike the font-sizes and colors. You can change those to fit your design.

---

The `x-defer` tag is only supported with Hyva theme module version 1.3.7 or higher.

If you're using an older version of the Hyva theme module, this tag will be ignored.

For about the [`x-defer` Apline plugin](https://docs.hyva.io/hyva-themes/view-utilities/alpine-defer-plugin.html) see our docs.

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
