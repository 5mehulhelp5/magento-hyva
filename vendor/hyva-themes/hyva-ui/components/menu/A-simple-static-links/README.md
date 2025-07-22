# Hyvä UI - menu.A - simple static links

[![License]](../../../LICENSE.md)
[![Hyva Supported Versions]](https://docs.hyva.io/hyva-ui-library/getting-started.html)
[![Tailwind Supported Versions]](https://tailwindcss.com/)
[![AlpineJS Supported Versions]](https://alpinejs.dev/)
[![Figma]](https://www.figma.com/@hyva)

This UI component renders menu links using a static array.

It's ideal for scenarios where you need different menus for desktop and mobile layouts.

## Usage - Template

1. Copy or merge the following files/folders into your theme:
   * `Magento_Theme/templates/html/header/menu/desktop.phtml`
2. Adjust the content and code to fit your own needs and save
3. Create your development or production bundle by running `npm run watch` or `npm run build-prod` in your
   theme's tailwind directory

## Preview

![preview-1](./media/A-simple-static-links.jpg "Preview of the desktop view")

## Notes

The font-family is not altered, unlike the font-sizes and colors. You can change those to fit your design.

It's recommended to pair Menu.A with Header.A for the best results (as shown in the previews).

However, Menu.A is also flexible and can be used with other UI Headers, including the Default Theme Header.

For the Default Theme Header specifically,
you'll need to apply the classes `order-2 sm:order-1 lg:order-2` to the top element of your Menu.A to maintain the intended layout.

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
