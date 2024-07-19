# HTML

## Syntax

- element
- opening tag
- content
- closing tag
- attribute
- comments

## Common Elements

- Boilerplate (doctype, html, head, body)
- Headings (h1,h2,etc.)
- Tool: Emmet
- Paragraphs (p)
- Anchor (a)
  - self-closing or void elements
  - relative vs. absolute paths
- Attributes
  - global
    - common: id, class, style
  - local/specific
    - common: value, src, href
- Image (img)
- Break (br)
- Scalable Vector Graphics (svg)
- Lists
- Div (div,block)
  - Semantic alternatives (header, main, footer, nav, address)
- Span (span, inline)
- Tool: W3C Validation
- Tables

## Conventions

### folder names, file names

- lowercase
- dasherize (words separated by dashes)
  - To convert (a string) to use hyphens as word separators.

### html tags

- lowercase

## Lab

- Exercise 1

## Form Elements

- Form
- Input
  - text
  - password
  - checkbox
  - radio
- Label
- Button
- Dropdown (select > option)

## Exercise 1 (layout.html)

Create a layout template including the common elements used in all pages.

1. Create a folder named **prs-design** and open it in Visual Studio Code
1. Create `layout.html`
1. Add Boilerplate (`doctype`, `html`, `head`, `body`)
1. Create an element to represent each area of the site (`header`, `main`, `nav`, "content" `section`)
1. Add this `svg` logo to the `header` followed by the name of the application "Purchase Request System"
   - https://logoipsum.com/artwork/245
   - click the copy icon and paste the `svg` code into your page
1. Add a link `a` with the content **Sign In**
1. Add these pages at the root of your project folder
   - Vendors (vendors.html, vendor-create.html, vendor-edit.html)
1. Add list `ul` of anchor `a` links inside `nav`
   - Requests (#)
   - Products (#)
   - Vendors (#)
   - Users (#)
1. Add a heading `h2` to the "main content" `section` of the page with the content **Home**

## Exercise 2 (vendors.html)

1. Add a heading `h2` to the "main content" `section` of the page with the content **Vendors**
1. Add a link `a` with the content **Create a vendor** that navigates to `vendor-create.html`
1. Create a card `div` for a vendor with an `address` element inside
1. Inside the `address` include:
   - vendor name in a `span`
   - vendor abbreviation in a `span`
   - surround/group the name and abbreviation in a div
   - vendor address with lines separated by `br`

## Exercise 3 (vendor-create.html)
