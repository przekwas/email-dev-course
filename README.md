# Notes

`caniemail.com` is a good resource for html and css compatability for email development cross-compatability

Tools to test across different email clients

-   Email on Acid
-   Testia
-   Litmus

Some factors that set email development apart from typical web dev:

-   Everything needs to be included in our HTML file
-   Our images need live or direct links
-   We can't link to external CSS files to style
-   We rely on inline CSS styling for all elements
    -   `<p style="color: #000000;">RIP My Life</p>`

How to design for all clients at once?

-   Start with a well-planned boilerplate for email clients
-   `<table>` elements instead of `<div>`
    -   MSO or Ghost Tables in Outlook
-   With mobile-friendly, 600px max-width designs to fit in Desktop, Web, and Mobile clients
-   By using `padding` _instead_ of `margin` for email compatability
-   Test, Test, Test

[https://www.litmus.com/email-client-market-share](https://www.litmus.com/email-client-market-share)

## HTML Stuffs

-   `<meta http-equiv="X-UA-Compatible" content="IE=edge">`
    -   literally just compatability for internet explorer
        -   and it's fucking doodoo lol
-   `<meta name="viewport" content="width=device-width,initial-scale=1.0">
    -   the viewable page should be displayed at the width of the device
    -   1.0 is the % of the viewport aka 100%
-   `<p>` default size is 16px in Chrome
-   Remember `<h1>` and other headers have some extra spacing versus paragraph text
    -   more of an issue in email dev
-   `<b>` is obvious and `<strong>` is bolded and important text compared to just bold
-   Same relationship for `<em>` aka emphasize and italics
-   Same relationship for `<ins>` and underline
-   `<big>` tag??
-   `<sub>` and `<sup>` for special script texts
-   `<mark>` for semantic highlight
-   `<del>` strikethrough and opposite of `<ins>`

-   `<a title="Stuff">`

    -   the `title` attr gives us some mouseover tooltip style text

-   HTML emails must link to urls directly online

    -   no relative file paths!!
    -   SEO can be done on web via filename, title, and alt text

-   `<textarea>` cols size is based on base font size
    -   e.g. `cols="10"` means it'll fit 10 (default 16px) characters across
    -   `rows="3"` means it can fit 3 rows of text

## CSS Stuffs

-   Font Family
    -   Fallback Fonts separated by commas
    -   `Brush Script MT, cursive;` your cursive font family
        -   not used much
-   400 font weight typically used for body text
-   `letter-spacing` nice for styling headings a bit
-   Pixels (px) are best for email design and layout
-   Hex colors are best for email

-   gradients still not the best in email dev but there are tricks you can do

    -   always do a `background-color` _and_ a `liner-gradient()` to make sure you got fallbacks
        -   same for a `background-image: url()`

-   `background-image` behaviors

    -   `background-repeat: no-repeat'` to toggle off default behaviour, and our fallback `background-color` will extend beyond if it's not repeated so a good trick to match the colors if you can
    -   `background-position: center;`
    -   `background-attachment: fixed;` fixed for "window" effect as you scroll by
        -   value `scroll` is the default aka it scrolls by

-   `box-shadow` has 4 vals

    -   first is horitonzal value
    -   second is vertical value
    -   third is blur radius
    -   fourth is the color

-   `<a>` pseudo classes order LVHA

    -   `L` a:link
    -   `V` a:visited
    -   `H` a:hover
    -   `A` a:active
    -   for "button" styling add `inset` to the :active pseudo class to make it look like it was clicked into the page
        -   also adjust box shadow opacity on pseudo states to give more life to the button styling

-   Stacked Icons are a go-to

-   `content-box` does not include borders in sizing/width of elements

    -   `border-box` does include them

-   Media Queries
    -   `@media screen and (max-width: 768px) {}`
        -   apply styles on a screen up 768px screen width and then stop
    -   **600px template typically in email** is the most common, so only 1 or 2 media queries needed

## Email Testing Services

-   Email Service Provider Platforms (i.e. MailChimp)
    -   subscriber lists, marketing blasts, statistics, and etc.
-   CAN-SPAM, CASL & GDPR Laws (address and unsubscribe)
    -   CAN-SPAM USA/FTC law
    -   CASL Canadian
    -   GDPR is EU
    -   Set rules & regulations for commercial emails and text messages.
-   Email Deliverability (to avoid ending up in spam)
    -   sender's ip address, open rate, click rate, sending domain's reputation, how the email is written/words used, not sending to old recipients
    -   having clean email code is important
        -   unclosed html tags, elements or js that don't work in email, having a normal design layout (i.e. no giant text/overlapping content), adding attachments, and using too many html comments
-   Merge Tags in ESps (i.e. subscriber first name)
    -   merge tags are placeholders or variables that represent info about the subscriber
    -   info from a CSV file with all the subscriber's details
    -   names, city, bday, interests, blah blah
    -   `Hi *|IFNAME|*` for MailChimp
-   Transactional Emails
    -   Sent in response to an action a user takes on a web or app
    -   Contain data that is specific to the user and are sent to individuals one at a time
-   Marketing Emails
    -   Promotional or Bulk Mail
    -   Same content delivered to many recipients simultaneously

## Responsive Emails

-   Template Width
    -   600px/640px - 800px
-   Template Height
    -   up to 3,000px
-   File Size
    -   up to 100kb
-   Tips

    -   email header up to 200px
    -   important details at first 350px in height
        -   "Above the fold" from newspaper idioms
        -   ain't nobody actually reading an entire email ad
    -   using responsive designs
    -   not using images to display all content
    -   images under 200kb each is best even though they're hosted online
    -   images up to 700kb made no impact on emails being delivered properly (EoA)
    -   under 2.5mb total for all images

-   Accessability
    -   design and code emails for people with:
        -   visual impairment
        -   cognitive or neurologically impairment
        -   physical limitations
    -   `aria-hidden` is common for screen reading stuff

## Boilerplate Stuffs

-   Because we have a billion different clients it's more important for making sure our shit renders correctly
-   Gotta use tables, sigh

-   `<html lang="en" dir="ltr">`

    -   `lang="en"` = declares the language of the document, helps with accessibility and screen readers
    -   `dir="ltr"` = text direction (left-to-right). Can also be `"rtl"` for right-to-left languages like Arabic/Hebrew

-   `xmlns:v="urn:schemas-microsoft-com:vml" xmlns:o="urn:schemas-microsoft-com:office:office"`

    -   Outlook/Office namespaces
    -   `v` = enables VML (Vector Markup Language) for shapes, background fills, buttons, etc.
    -   `o` = Office-specific namespace for Outlook hacks like DPI scaling fixes and OfficeDocumentSettings
    -   Totally redundant for normal web but critical for Outlook desktop apps

-   `<meta http-equiv="Content-Type" content="text/html; charset=utf-8">`

    -   Declares document type and encoding
    -   Needed for email clients that choke without explicit `charset`
    -   Somewhat redundant in HTML5 but still included for email boilerplates

-   `<meta http-equiv="X-UA-Compatible" content="IE=edge">`

    -   Forces IE to use the newest rendering engine available
    -   Basically does nothing in modern browsers but helps prevent quirks mode

-   `<meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=yes">`

    -   Mobile scaling behavior
    -   Ensures email adapts to device width
    -   `user-scalable=yes` = allows pinch-to-zoom (sometimes set to `no` in marketing emails to lock layout)

-   `<meta name="format-detection" content="telephone=no, date=no, address=no, email=no, url=no">`

    -   iOS/Apple Mail tries to auto-link phone numbers, dates, addresses, etc.
    -   This disables auto-linking so they don’t break layouts or turn into blue links

-   `<meta name="X-apple-disable-message-reformatting">`

    -   Apple Mail iOS will sometimes auto-resize/reformat email content
    -   This disables that behavior so your layout stays intact

-   `<meta name="color-scheme" content="light dark">`  
    `<meta name="supported-color-schemes" content="light dark">`
    -   Hints to Apple Mail and some modern clients that your email supports both light and dark mode
    -   Helps prevent forced color inversion
    -   Only supported by a few clients, but good practice now

## CSS Reset Stuffs

-   `table { border-spacing: 0; border-collapse: collapse; }`

    -   Prevents extra gaps between table cells
    -   Critical since emails are 99% table-based

-   `td { padding: 0; }`

    -   Removes default padding from table cells
    -   Keeps layouts pixel-perfect across clients

-   `p { font-size: 16px; }`

    -   Standardizes paragraph size
    -   Helps avoid tiny text in some clients

-   `img { border: 0; }`

    -   Prevents linked images from getting a default blue border in Outlook
    -   Often paired with `display: block;` or `line-height: 0;` so stacked images don’t create weird spacing

-   `a { text-decoration: none; color: #3d3d3d; font-size: 16px; }`

    -   Kills the default underline and sets consistent font size/color
    -   Inline overrides usually required in production

-   `.content { line-height: 20px; font-size: 16px; }`

    -   Example class, not required
    -   Used to keep body copy neat and consistent

-   `.ExternalClass { width: 100%; }`

    -   Outlook.com (the web client) wraps email content in a special `.ExternalClass`
    -   Forces it to take full width

-   `.ExternalClass, .ExternalClass p, .ExternalClass span, .ExternalClass font, .ExternalClass td, .ExternalClass div { line-height: 100%; }`

    -   Fixes spacing issues unique to Outlook.com
    -   Forces consistent line-height across all nested elements

-   `a[x-apple-data-detectors='true'] { color: inherit !important; text-decoration: inherit !important; }`
    -   Stops iOS from turning phone numbers, dates, or addresses into default blue links
    -   The `!important` is required because Apple Mail overrides otherwise

## Media Query Stuffs

-   `@media screen and (max-width: 599.98px) { ... }`

    -   Targets screens **under ~600px** wide (common mobile breakpoint in email dev)
    -   The `.98` trick avoids overlap with next range (prevents flickering at exact `600px`)
    -   Example:
        -   `.background-test { background-color: #ff0000; }`
            -   Just a demo — would force red background on smaller screens
        -   `.font-size-test { font-size: 40px !important; }`
            -   `!important` needed because inline styles normally win in email
            -   Lets you scale text up/down for mobile

-   `@media screen and (max-width: 399.98px) { ... }`

    -   Extra-narrow screen breakpoint (older/small phones)
    -   Often left empty until you need to tweak really tiny devices
    -   Future-proof spot for overrides like stacking elements, shrinking text, or hiding less important sections

-   `<!--[if mso]> ... <![endif]-->`

    -   Conditional comments that only run in Microsoft Outlook (Word-based rendering engine)
    -   Lets you feed Outlook-specific fixes without breaking other clients

-   `<o:OfficeDocumentSettings><o:PixelsPerInch>96</o:PixelsPerInch></o:OfficeDocumentSettings>`

    -   Fix for DPI scaling issues in Outlook 2007–2013
    -   On high-res screens or when users change Windows display settings (e.g. larger text for eyesight), Outlook can scale emails incorrectly
    -   Forces Outlook to render at **96 PPI** (standard pixel density) so layouts don’t blow up
    -   Also prevents “96” characters from showing in some weird clients like **T-Online**

-   `<noscript><xml> ... </xml></noscript>`

    -   Wrapped in `<noscript>` + `<xml>` so non-Outlook clients just ignore it
    -   Outlook reads it through the `xmlns:o` namespace (`urn:schemas-microsoft-com:office:office`)

-   `<!--[if mso]> ... <![endif]-->`

    -   Conditional CSS block for Microsoft Outlook only
    -   Targets quirks of Word’s rendering engine that ignore or override normal CSS

-   `body { background-color: #dde0e1 !important; }`

    -   Forces background color in Outlook (which often strips `body` styles)

-   `body, table, td, p, a { font-family: Arial, Helvetica, sans-serif !important; }`

    -   Outlook defaults to Times New Roman if it can’t parse font-family
    -   This enforces a safe fallback stack

-   `table { ... }`
    -   `border-spacing: 0 !important;`  
        Prevents extra gaps between table cells (needed even though you collapse elsewhere)
    -   `border-collapse: collapse !important;`  
        Ensures tables render tightly (Outlook loves inserting ghost gaps)
    -   `line-height: 100% !important;`  
        Normalizes line-height since Outlook may miscalculate text spacing inside tables
    -   `mso-line-height-rule: exactly !important;`  
        Outlook-specific property — locks line height so text doesn’t stretch
    -   `mso-table-lspace: 0pt !important; mso-table-rspace: 0pt !important;`  
        Removes default left/right table cell padding in Outlook (it adds invisible spacing otherwise)
