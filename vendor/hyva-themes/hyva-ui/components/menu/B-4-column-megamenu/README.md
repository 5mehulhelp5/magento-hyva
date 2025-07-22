# Hyvä UI - menu.B - 4 column megamenu

[![License]](../../../LICENSE.md)
[![Hyva Supported Versions]](https://docs.hyva.io/hyva-ui-library/getting-started.html)
[![Tailwind Supported Versions]](https://tailwindcss.com/)
[![AlpineJS Supported Versions]](https://alpinejs.dev/)
[![Figma]](https://www.figma.com/@hyva)

This is a desktop menu showing a 4 column megamenu with the possibility to add a static block. 

## Usage - Template

1. Copy or merge the following files/folders into your theme:
   * `Magento_Theme/templates/html/header/menu/desktop.phtml`
   * `Magento_Theme/layout/default.xml`
2. Adjust the content and code to fit your own needs and save
3. Create your development or production bundle by running `npm run watch` or `npm run build-prod` in your
   theme's tailwind directory

### Configuration Options

This UI component offers customization options without modifying the corresponding phtml files.

To configure this UI component,
utilize the provided options as outlined in the `src/Magento_Theme/layout/default.xml` file.

| Option Name                    | Type    | Available Values | Default | Description                                          |
| ------------------------------ | ------- | ---------------- | ------- | ---------------------------------------------------- |
| `open_top_level_menu_on_hover` | boolean | true, false      | true    | If the top level menu item should also open on hover |
| `show_top_level_all_link`      | boolean | true, false      | true    | Show view all link for top level                     |
| `top_menu_cta_item`            | string  |                  |         | Top Menu Item to Highlight _#1_                      |

> #1: The xml code includes a sample use case for `top_menu_cta_item`,
> this only takes effect if the top level menu item has no child menu items

### Display CMS Content in Top Level Menu Panel

The menu can display custom content from CMS blocks for your top level categories.

Here's how to add CMS content to your menu:

1. **Create CMS Blocks:** Build your desired content using CMS blocks.
2. **Assign Block Identifiers:** Use the identifier format `desktop-menu-category-[ID]`, where `[ID]` is replaced with the actual ID of your category.

#### Finding Category IDs:

There are two ways to locate the category ID:

* **Admin Backend:**  Go to your admin panel and find the category ID listed there.
* **Frontend HTML:**  Alternatively, you can inspect the category panel's HTML code in your frontend view and look for the element's ID attribute. 

## Preview

| Type                |              | with CMS Block |
| ------------------- | ------------ | -------------- |
| Default             | ![preview-1] |                |
| Open with CMS block | ![preview-2] | ![preview-3]   |

[preview-1]: ./media/B-4-column-megamenu.jpg "Preview of the Menu on desktop view"
[preview-2]: ./media/B-4-column-megamenu-open.jpg "Preview of the Menu Open on desktop view"
[preview-3]: ./media/B-4-column-megamenu-open-with-block.jpg "Preview of the Menu Open on desktop view with a CMS block"

## Notes

The font-family is not altered, unlike the font-sizes and colors. You can change those to fit your design.

It's recommended to pair Menu.B with Header.C for the best results (as shown in the previews).

However, Menu.B is also flexible and can be used with other UI Headers, including the Default Theme Header.

For the Default Theme Header specifically,
you'll need to apply the classes `order-2 sm:order-1 lg:order-2` to the top element of your Menu.B to maintain the intended layout.

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
