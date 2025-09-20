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

[https://www.litmus.com/email-client-market-share](https://www.litmus.com/email-client-market-share)

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

- `<textarea>` cols size is based on base font size
  - e.g. `cols="10"` means it'll fit 10 (default 16px) characters across
  - `rows="3"` means it can fit 3 rows of text

## CSS Stuffs

- Font Family
  - Fallback Fonts separated by commas 
  - `Brush Script MT, cursive;` your cursive font family
    - not used much
- 400 font weight typically used for body text
- `letter-spacing` nice for styling headings a bit
  
- Pixels (px) are best for email design and layout
- Hex colors are best for email

- gradients still not the best in email dev but there are tricks you can do
  - always do a `background-color` *and* a `liner-gradient()` to make sure you got fallbacks
    - same for a `background-image: url()`

- `background-image` behaviors 
  - `background-repeat: no-repeat'` to toggle off default behaviour, and our fallback `background-color` will extend beyond if it's not repeated so a good trick to match the colors if you can
  - `background-position: center;` 
  - `background-attachment: fixed;` fixed for "window" effect as you scroll by
    - value `scroll` is the default aka it scrolls by

- `box-shadow` has 4 vals
  - first is horitonzal value
  - second is vertical value
  - third is blur radius
  - fourth is the color

- `<a>` pseudo classes order LVHA
  - `L` a:link
  - `V` a:visited
  - `H` a:hover
  - `A` a:active
  - for "button" styling add `inset` to the :active pseudo class to make it look like it was clicked into the page
    - also adjust box shadow opacity on pseudo states to give more life to the button styling

- Stacked Icons are a go-to

- `content-box` does not include borders in sizing/width of elements
  - `border-box` does include them

- Media Queries
  - `@media screen and (max-width: 768px) {}`
    - apply styles on a screen up 768px screen width and then stop
  - **600px template typically in email** is the most common, so only 1 or 2 media queries needed

## Email Testing Services

- Email Service Provider Platforms (i.e. MailChimp)
- CAN-SPAM, CASL & GDPR Laws (address and unsubscribe)
- Email Deliverability (to avoid ending up in spam)
- Merge Tags in ESps (i.e. subscriber first name)