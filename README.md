# Notes

`caniemail.com` is a good resource for html and css compatability for email development cross-compatability

Tools to test across different email clients
- Email on Acid
- Testia
- Litmus

Some factors that set email development apart from typical web dev:
- Everything needs to be included in our HTML file
- Our images need live or direct links
- We can't link to external CSS files to style
- We rely on inline CSS styling for all elements
  - `<p style="color: #000000;">RIP My Life</p>`

How to design for all clients at once?
- Start with a well-planned boilerplate for email clients
- `<table>` elements instead of `<div>`
  - MSO or Ghost Tables in Outlook
- With mobile-friendly, 600px max-width designs to fit in Desktop, Web, and Mobile clients
- By using `padding` *instead* of `margin` for email compatability
- Test, Test, Test

[[text](https://www.litmus.com/email-client-market-share)](https://www.litmus.com/email-client-market-share)

## HTML Stuffs

- `<meta http-equiv="X-UA-Compatible" content="IE=edge">`
  - literally just compatability for internet explorer 
    - and it's fucking doodoo lol
- `<meta name="viewport" content="width=device-width,initial-scale=1.0">
  - the viewable page should be displayed at the width of the device
  - 1.0 is the % of the viewport aka 100%
- `<p>` default size is 16px in Chrome
- Remember `<h1>` and other headers have some extra spacing versus paragraph text
  - more of an issue in email dev
- `<b>` is obvious and `<strong>` is bolded and important text compared to just bold
- Same relationship for `<em>` aka emphasize and italics
- Same relationship for `<ins>` and underline
- `<big>` tag??
- `<sub>` and `<sup>` for special script texts
- `<mark>` for semantic highlight
- `<del>` strikethrough and opposite of `<ins>`

- `<a title="Stuff">`
  - the `title` attr gives us some mouseover tooltip style text

- HTML emails must link to urls directly online
  - no relative file paths!!
  - SEO can be done on web via filename, title, and alt text
  - 