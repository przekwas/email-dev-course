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

## Containing Divs, Inline Styling, Redundancy, and Fallbacks

-   `<body class="body" xml:lang="en" style="margin:0; padding:0; min-width:100%; background-color:#dde0e1">`

    -   `margin:0; padding:0;` = strips default browser spacing
    -   `min-width:100%;` = makes sure background spans full viewport
    -   `background-color:#dde0e1;` = fallback gray background for clients that ignore container styles
    -   `xml:lang="en"` = alternate language declaration (used in some XML-based parsers and screen readers)

-   Outer `<div style="width:100%; table-layout:fixed; background-color:#dde0e1; ...">`

    -   Acts as the "real body" wrapper since not all clients respect `<body>` styles
    -   `table-layout:fixed;` = stabilizes rendering in table-heavy layouts
    -   `color`, `font-family`, `font-size` repeated here → redundancy on purpose so Outlook / Gmail / Yahoo don’t override
    -   `margin:0 auto 40px;` = centers content block and adds spacing at bottom

-   Inner `<div style="max-width:600px; background-color:#fafdfe; ...">`
    -   The main content container (max width = standard 600px email template)
    -   `margin:0 auto;` = centers this container horizontally
    -   `background-color:#fafdfe;` = white-ish fallback so text is readable even if outer bg fails
    -   `font-family` + `font-size` repeated → ensures copy renders correctly even if parent style is stripped
    -   `box-shadow:0 0 10px rgba(0,0,0,0.2);` = decorative; supported in some modern clients but gracefully ignored elsewhere
    -   Fallback philosophy: repeat essential styles (color, font, bg) at multiple levels so if one client drops outer CSS, the inner container still looks okay

## Preheader Text / Preview Text

-   Preheader = the little preview line of text that shows up in inboxes next to/under the subject line

    -   Typically **35–190 characters**, sweet spot is **85–100 characters**
    -   Acts as a "second subject line" → boosts open rates

-   `<div style="font-size:0; color:#fafdfe; ... display:none; ...">`

    -   Hidden text block for preheader content
    -   Styled to be invisible in the actual email body:
        -   `font-size:0; line-height:0px; max-width:0; max-height:0; opacity:0; overflow:hidden; display:none;`
        -   `mso-hide:all;` = hides from Outlook desktop
        -   `color:#fafdfe;` = matches background color in case client ignores `display:none`

-   Why all the random HTML entities (`&zwnj; &nbsp; &#847;` etc)?

    -   They act as **padding text** so the real email content doesn’t leak into the inbox preview
    -   Different inboxes (Gmail, Outlook, Apple Mail) will sometimes pull in extra characters if your preheader is too short
    -   Adding invisible junk characters pushes your real email body out of preview range

-   Best practice:
    -   Always include a preheader for marketing or transactional emails
    -   Hide it from the design but keep it in code
    -   Fill the rest of the space with invisible entities so only your curated text is previewed

## Tables in Email Templates

-   Tables = the backbone of email layout (because `<div>` support is trash in Outlook)
-   Old-school way:

    ```html
    <table
    	border="1"
    	cellspacing="0"
    	cellpadding="0"
    >
    	<tr>
    		<td>Cell 1</td>
    	</tr>
    </table>
    ```

    -   `border="1"` = adds a 1px border (default browser style, not flexible)
    -   `cellspacing="0"` = removes spacing between cells
    -   `cellpadding="0"` = removes padding inside each `<td>`
    -   ✅ Works everywhere but dated / attribute-heavy

-   Modern CSS way:

    ```html
    <table style="border-collapse: collapse">
    	<tr>
    		<td style="padding: 0">Cell 1</td>
    	</tr>
    </table>
    ```

    -   `border-collapse: collapse;` = cells share borders, no spacing between them
    -   `padding: 0;` = replaces `cellpadding="0"`
    -   Cleaner → relies on CSS instead of HTML attributes

-   Why CSS solution is preferred:
    -   More consistent with web standards
    -   Easier to manage styling inline
    -   Avoids mixing presentational attributes (`cellpadding`, `cellspacing`) with structure
    -   Still fully supported in Outlook and other picky clients

## Main Template Table

-   `<table align="center" role="presentation" ...>`

    -   `align="center"` = legacy way to center tables (still respected by Outlook)
    -   `role="presentation"` = accessibility → signals to screen readers that the table is for layout, not data

-   `style="border-spacing:0; border-collapse:collapse; ..."`

    -   `border-spacing:0; border-collapse:collapse;`
        -   Prevents gaps/borders between table cells
        -   Outlook-safe reset
    -   `color:#3d3d3d; font-family:Arial, Helvetica, sans-serif; font-size:16px;`
        -   Redundancy → sets default text styling for the whole email
        -   Ensures consistent fallback when inline styles are stripped
    -   `background-color:#fafdfe;`
        -   Default white background for main content area
        -   Matches common email designs
    -   `margin:0 auto;`
        -   Centers table in client window
    -   `padding:0;`
        -   Prevents unintended spacing around table (important in Outlook)
    -   `width:100%; max-width:600px;`
        -   Forces full width on mobile while capping design at **600px**
        -   Standard practice for responsive email templates

-   ⚖️ Best practice:
    -   Main template table = **600px max-width, centered, role="presentation"**
    -   Use padding on **nested tables** or cells for spacing — keep outer container stripped to zero padding for control
    -   Inline styles for every nested element, since some clients ignore global CSS

## Outlook “Ghost Table” Wrapper

-   Why this exists

    -   Outlook (Word engine) ignores `max-width` on the main table and can break centering.
    -   A **ghost table** inside an `<!--[if mso]> ... <![endif]-->` block gives Outlook a fixed **600px** container without affecting mobile clients.

-   Structure recap

    ```html
    <!--[if mso]>
      <table width="600" align="center" role="presentation" style="border-spacing:0; border-collapse:collapse; color:#3d3d3d">
        <tr><td style="padding:0">
    <![endif]-->

    <table
    	align="center"
    	role="presentation"
    	style="border-spacing:0; border-collapse:collapse; color:#3d3d3d; font-family:Arial, Helvetica, sans-serif; font-size:16px; background-color:#fafdfe; margin:0 auto; padding:0; width:100%; max-width:600px;"
    >
    	<tr>
    		<td style="padding:0">
    			<table
    				width="100%"
    				role="presentation"
    				style="border-spacing:0"
    			>
    				<tr>
    					<td style="padding:10px; background-color:#c0c0ff">
    						<h1 style="text-align:center; font-size:30px; margin:0">This is some text.</h1>
    					</td>
    				</tr>
    			</table>
    		</td>
    	</tr>
    </table>

    <!--[if mso]>
        </td></tr></table>
    <![endif]-->
    ```

-   Key points

    -   `<!--[if mso]> ... <![endif]-->`  
        Outlook-only wrapper. Mobile/webmail clients don’t see it, so they use the responsive `width:100%; max-width:600px;` table instead.
    -   `width="600"` on the ghost table  
        Use the HTML attribute for Outlook reliability (attributes tend to win over CSS in Word).
    -   `align="center"` on the ghost table  
        Legacy centering Outlook still respects.
    -   **Do content inside inner rows**  
        Keep the outer responsive table’s first `<td>` clean and put actual content in a nested 100%-width table → avoids spacing/line-height quirks in Outlook/Gmail.
    -   `role="presentation"`  
        Accessibility hint: this is layout, not data.
    -   `border-spacing:0; border-collapse:collapse;`  
        Reduces gaps/borders across clients (especially Outlook).
    -   Padding strategy  
        Put padding on **inner `<td>`s** (like your `padding:10px` cell), not on the outer container, for predictable spacing everywhere.

-   Common pitfalls (and fixes)

    -   **Mobile squish or overflow**  
        Ensure the responsive table has `width:100%; max-width:600px;` and that images use `display:block; max-width:100%; height:auto;`.
    -   **Unexpected gaps between rows**  
        Confirm `line-height` on text elements and avoid empty `\n` text nodes between table tags (minify/inline tidy).
    -   **Double padding**  
        Don’t add padding on both the outer `<td>` and the inner content cell—pick one (inner cell).

-   TL;DR
    -   Ghost table = fixed 600px for Outlook only.
    -   Responsive table = `width:100%` + `max-width:600px` for everyone else.
    -   Nest content rows inside a 100% inner table; pad those cells, not the outer frame.

## Dark Mode Support

-   `:root { color-scheme: light dark; supported-color-schemes: light dark; }`

    -   Declares to clients (Apple Mail, iOS Mail, some modern apps) that your email supports **light and dark mode**
    -   Important: the `s` in `supported-color-schemes` is required
    -   Not all clients respect this, but it helps prevent forced color inversions

-   `@media (prefers-color-scheme: dark) { ... }`

    -   Modern CSS media query for users who have dark mode enabled
    -   Supported in Apple Mail, iOS Mail, some Android apps — **not Outlook desktop**

-   Inside dark mode query:

    -   `body, table { background:#2d2d2d !important; color:#ffffff !important; }`
        -   Forces dark background + light text
        -   `!important` needed because inline styles win otherwise
    -   `.darkmode-transparent { background-color:transparent !important; }`
        -   Utility class → lets specific sections stay transparent even in dark mode
    -   `[data-ogsc] body, table { ... }`
        -   `[data-ogsc]` = **Outlook.com (webmail) + Outlook apps hack**
        -   Ensures dark mode styles apply in those clients
    -   `[data-ogsc] .darkmode-transparent { background-color:transparent !important; }`
        -   Same transparent override, but scoped for Outlook web/app

## Extra Best Practices & Gotchas

-   Always set **both light and dark backgrounds** (fallback + override)

    -   Use `[data-ogsc]` selectors for Outlook.com dark mode
    -   Test in Apple Mail, Gmail app, and Outlook web since each inverts differently

-   **No dead links** — even in testing

    -   Email on Acid and some clients will break previews if `href="#"` or empty URLs are used
    -   Always point to a real endpoint (can be dummy but valid)

-   **Images require both** inline style and attribute for cross-client rendering

    -   Example:  
        `<img src="example.jpg" width="600" style="width:100%; max-width:600px; height:auto; display:block;" alt="..." />`
    -   `width` attribute = makes images render in Outlook
    -   `style="width:100%;"` = makes them responsive on mobile/webmail

-   **Unique links per instance**

    -   Helps testing/tracking — some clients merge duplicate links in previews/clicks

-   Inline styles on every element

    -   Don’t rely on inheritance — add `font-size`, `line-height`, `color`, etc. directly
    -   Especially for headers `<h1>`–`<h6>`, `<p>`, and `<td>` content

-   Anchors inside `<p>`?

    -   Often safer to wrap `<a>` in `<p>` for consistent spacing across clients
    -   Prevents inline anchor text from breaking line-height or margins

-   Links showing blue randomly?

    -   Fix with both:  
        `style="color:#3d3d3d; color:inherit; text-decoration:none;"`
    -   The `inherit` lets it pick up parent `<p>` styles and kills auto-blue styling

-   Stop auto-linking addresses

    -   Insert invisible zero-width space: `&#8203;`
    -   Example: `123&#8203; Street Road, City, State 55555`
    -   Prevents Apple Mail/iOS from turning addresses into blue links

-   Image responsiveness
    -   Always use **both attribute + inline style**
    -   `width="600"` → Outlook desktop needs it  
        `style="width:100%;"` → responsive in mobile/web clients
    -   Add `height:auto; display:block;` for proper scaling + removing default gaps

## Responsive Table Layouts for Email Columns

-   fixed: multiple columns but not mobile friendly
-   scalable: single column, the same across devices
-   fluid: a single column typically with a lot of text and it flexes content based on device width
-   hybrid: multiple columns with fixed widths but tables adjust/collapse based on screen size
-   fluid-hybrid/responsive: multiple columns which collpase based on screen size and use responsive/fluid css styling with media queries in clients allowing it

-   <td class="column-wrapper" style="padding: 0; font-size: 0;">
      -   wraps the two tables in a 2 col layout for example
      -   the font-size 0 is a trick to make the columns display inline next to each other

## Responsive Two-Column Pattern (Fluid-Hybrid)

-   **Pattern goal**

    -   Two columns on desktop (600px container → ~300px each), automatic **stacking on mobile** without needing media queries.
    -   Works via `display:inline-block` + `width:100%` + `max-width:300px`.

-   **Wrapper row**

    -   `<td class="column-wrapper" style="padding:0; font-size:0; background-color:#b7c0ba">`
        -   `font-size:0` kills the whitespace that appears between inline-block columns.
        -   Put **all inter-column spacing inside child cells** (padding) so mobile stacks cleanly.

-   **Each column table**

    -   `class="column column-one-half" width="100%" role="presentation"`
    -   Inline styles:
        -   `display:inline-block;` → sit side-by-side when space allows.
        -   `width:100%; max-width:300px;` → each column caps at 300px inside a 600px container, but becomes 100% on narrow screens (stacks).
        -   `vertical-align:top;` → prevents bottom alignment oddities when columns have different heights.
        -   Background & text colors may be repeated here for **redundancy** across clients.

-   **Gutters / spacing**

    -   Prefer **padding on inner `<td>`** (e.g., `padding:20px`) instead of margins (margin support is spotty).
    -   If you need a visible gap **between** columns, use:
        -   Extra padding on the left/right inner cells, or
        -   A thin spacer column (3-10px) as another inline-block table (older pattern).

-   **Images inside columns**

    -   Wrap in an anchor for tappable area.
    -   Use **attribute + inline CSS** for cross-client sizing:
        -   `<img width="260" style="width:100%; max-width:260px; height:auto; display:block; border:0" ... />`
    -   Always include `alt` (and `title` if desired).

-   **Headings / copy**

    -   Inline all key text styles (`font-size`, `line-height`, `color`, `text-align`) on each element (`<h1>…</h1>`, `<p>…</p>`).
    -   Set `margin:0` on headings to avoid mystery whitespace across clients.

-   **Accessibility**

    -   `role="presentation"` on layout tables.
    -   Meaningful `alt` text; avoid using images of text where possible.
    -   Keep reading order logical (see “stacking order” below).

-   **Stacking order (mobile)**

    -   This fluid-hybrid pattern stacks columns in **source order** (left column first).
    -   To reverse on mobile without media queries, wrap the two column tables in a parent with `dir="rtl"` and give each column `dir="ltr"` (advanced pattern). Otherwise, control order by HTML source.

-   **Outlook gotchas**

    -   The overall 600px container should already be inside the **ghost table** for Outlook desktop.
    -   Keep column padding on inner `<td>` elements; avoid padding on the outer container `<td>` to reduce Outlook spacing bugs.

-   **Optional media query refinements**

    -   You can still add:
        ```css
        @media screen and (max-width: 599.98px) {
        	.column {
        		max-width: 100% !important;
        	}
        	.padding {
        		padding: 16px !important;
        	}
        	.column h1,
        	.column p {
        		font-size: larger !important;
        		line-height: 1.4 !important;
        	}
        }
        ```
        for extra polish in clients that support media queries.

-   **TL;DR**
    -   `font-size:0` on the **wrapper** td to remove inline-block gaps.
    -   Each **column** = `display:inline-block; width:100%; max-width:300px; vertical-align:top;`.
    -   Put spacing in **inner cell padding**; inline all critical text/image styles.

#### SIMPLE TWO COLUMNS — REVERSED (DIR TRICK)

-   **What this does**

    -   Add `dir="rtl"` to the **wrapper td** → inline‐block columns render **right→left**, so the _second_ column appears first on desktop.
    -   Add `dir="ltr"` to any **textual column/table** so Latin text reads normally (prevents punctuation mirroring and bidi quirks).

-   **Why use it**

    -   Reorders columns **without media queries** and with high client support (great for Outlook desktop).
    -   Mobile still stacks columns in **source order**; the visual desktop order is swapped by `dir`.

-   **Key styles in this pattern**

    -   `.column-wrapper { font-size:0; text-align:center; }`
        -   `font-size:0` removes the whitespace between `inline-block` columns.
        -   Centering helps with odd client spacing.
    -   `.column { display:inline-block; width:100%; max-width:300px; vertical-align:middle; }`
        -   `inline-block` lets columns sit side-by-side; `max-width` caps each at ~half of a 600px container.
        -   `vertical-align:middle` keeps uneven column heights visually aligned.
    -   `.padding { padding:20px; }`
        -   Put spacing on **inner td**, not on the outer wrapper (safer in Outlook).

-   **Accessibility**

    -   Use `role="presentation"` on layout tables.
    -   Ensure **reading order** in the HTML matches the order you want screen readers to follow (dir flips _visual_ order, not DOM order).

-   **Client quirks & tips**

    -   **Outlook desktop**: this dir trick works; keep the whole layout inside the 600px **ghost table** wrapper for consistent centering.
    -   **Gmail / Apple Mail**: respect `dir`; still add responsive media queries if you need extra mobile tweaks.
    -   Add `dir="ltr"` on any column that contains **Latin text** or numbers; otherwise symbols, punctuation, and inline icons can appear mirrored or repositioned.
    -   Avoid margins for gutters; use **cell padding** or a spacer cell if you must create visible gaps.

-   **Images**

    -   Use both attribute + inline CSS for sizing:
        ```html
        <img
        	width="260"
        	style="width:100%; max-width:260px; height:auto; display:block; border:0"
        	alt="Image Description"
        />
        ```
    -   Wrap images in `<a>` to expand the tap area.

-   **Optional media query refinement**
    ```css
    @media screen and (max-width: 599.98px) {
    	.column-wrapper {
    		padding: 15px 0 !important;
    	}
    	.padding {
    		padding: 5px 20px 0 20px !important;
    	}
    	.column {
    		max-width: 100% !important;
    	} /* force full width if needed */
    }
    ```

````markdown
#### Align Table Columns for MSO (Outlook Desktop)

-   **Why this exists**

    -   Outlook desktop (Word rendering engine) does not always respect `display:inline-block` for columns.
    -   Solution: wrap each column in an Outlook-only table cell using conditional comments (`<!--[if mso]>` … `<![endif]-->`).
    -   This creates a predictable side-by-side layout in Outlook without breaking mobile/web clients.

-   **Structure**

    ```html
    <!--[if mso]>
      <table width="100%" style="border-spacing:0;" role="presentation">
        <tr>
          <td width="300" valign="middle" style="padding:0;">
    <![endif]-->

    <!-- Column 1 table -->
    <table
    	class="column column-one-half"
    	width="100%"
    	style="max-width:300px; display:inline-block; vertical-align:middle;"
    	role="presentation"
    >
    	...
    </table>

    <!--[if mso]>
          </td>
          <td width="300" valign="middle" style="padding:0;">
    <![endif]-->

    <!-- Column 2 table -->
    <table
    	class="column column-one-half"
    	width="100%"
    	style="max-width:300px; display:inline-block; vertical-align:middle;"
    	role="presentation"
    >
    	...
    </table>

    <!--[if mso]>
          </td>
        </tr>
      </table>
    <![endif]-->
    ```
````

-   **Key parts**

    -   `<!--[if mso]> ... <![endif]-->`
        Conditional comments: only Outlook desktop sees this wrapper table.
    -   `<td width="300" valign="middle">`
        Defines fixed-width columns and vertical alignment specifically for Outlook.
    -   Non-Outlook clients use the **inline-block + max-width** responsive pattern as normal.

-   **Best practices**

    -   Keep padding at `0` on Outlook `<td>` wrappers; put spacing inside the **inner column `<td>`** (`.padding` class).
    -   Use both **attribute + CSS** for widths:

        -   `width="260"` + `style="width:100%; max-width:260px;"` for images.
        -   `width="100%" max-width:300px; display:inline-block;` for tables.

    -   Vertical alignment:

        -   `valign="middle"` in the MSO `<td>`.
        -   `vertical-align:middle;` inline CSS in the normal column table.

-   **Fallback behavior**

    -   Mobile clients stack columns naturally because of `width:100%; max-width:300px;`.
    -   Outlook desktop respects the fixed `width="300"` from the ghost `<td>` cells, ensuring perfect 2-column side-by-side alignment.

-   **TL;DR**

    -   Outlook hates inline-block columns → give it its own ghost table structure with fixed `<td width>` cells.
    -   Non-Outlook clients ignore the MSO wrappers and just render the responsive columns.

dir ltr/rtl can work fine in outlook but we can do it in mso conditionals if we want it only reversed in outlook

### HTML Email Elements

Outlook

-   only 2 diff font weights
    -   0-599 normal weight, anything 600+ is bold
-   no cursive families?

## VML in Outlook — Shapes, Images, and Units (Cheat-Sheet + Fixes)

-   **Namespaces you need**

    -   Add this to your `<html …>` if you use `w:anchorlock`:
        -   `xmlns:w="urn:schemas-microsoft-com:office:word"`
    -   Already using:
        -   `xmlns:v="urn:schemas-microsoft-com:vml"` (VML)
        -   `xmlns:o="urn:schemas-microsoft-com:office:office"` (Office)

-   **px vs pt (Word/VML uses points)**

    -   `16px = 12pt` (web defaults vs Word defaults)
    -   `px × 0.75 = pt`
    -   `pt × 1.333 = px`
    -   In VML `style="width:…; height:…"`: prefer **pt** for Outlook consistency (but px often “works”)

-   **Elements (common)**

    -   `v:rect` — rectangle
    -   `v:oval` — circle/ellipse
    -   `v:roundrect` — rounded rectangle (**note:** you had `v:roundreact` → typo)
    -   `v:image` — image element (VML-only; no `alt`)
    -   `v:fill` — image/color fill for a shape (used as a child of `v:rect/roundrect`)
    -   `v:textbox` — text inside a shape (use `inset="l,t,r,b"`)
    -   `w:anchorlock` — keeps the VML “button” hyperlink from being altered by Outlook

-   **Useful attributes**

    -   `fill="t|f"` / `fillcolor="#RRGGBB"` — background fill on shapes
    -   `stroke="t|f"` / `strokecolor="#RRGGBB"` / `strokeweight="Xpt"` — borders on shapes
    -   `arcsize="%"` — corner radius on `v:roundrect` (e.g., `arcsize="40%"`)
    -   `href="https://…"` — on `v:roundrect` to make the entire shape clickable
    -   `inset="0,0,0,0"` — padding inside `v:textbox`

-   **Corrected snippets from your examples**

    -   **Solid rectangle (100×100)**

        ```html
        <!--[if mso]>
        	<v:rect
        		fill="t"
        		fillcolor="#546c94"
        		stroke="f"
        		style="width:75pt; height:75pt"
        	></v:rect>
        <![endif]-->
        ```

        -   `100px ≈ 75pt`

    -   **Stroked rectangle**

        ```html
        <!--[if mso]>
        	<v:rect
        		fillcolor="#546c94"
        		stroke="t"
        		strokecolor="#00ff00"
        		strokeweight="6pt"
        		style="width:56.25pt; height:56.25pt"
        	>
        	</v:rect>
        <![endif]-->
        ```

        -   `75px ≈ 56.25pt`

    -   **Rounded “button” with centered text**

        ```html
        <!--[if mso]>
        	<v:roundrect
        		href="https://example.com"
        		style="height:40pt; width:120pt"
        		arcsize="40%"
        		fillcolor="#546c49"
        		strokecolor="#000000"
        		strokeweight="4pt"
        	>
        		<w:anchorlock />
        		<v:textbox inset="0,0,0,0">
        			<center style="font-family:Arial, Helvetica, sans-serif; font-weight:400; font-size:18pt; color:#ffffff; line-height:20pt;">
        				BUTTON
        			</center>
        		</v:textbox>
        	</v:roundrect>
        <![endif]-->
        ```

        -   **Fix:** tag name is `v:roundrect` (not `v:roundreact`)
        -   Include `xmlns:w="urn:schemas-microsoft-com:office:word"` in `<html …>`

    -   **Plain VML image**

        ```html
        <!--[if mso]>
        	<v:image
        		src="https://…/image.jpg"
        		style="width:337.5pt; height:249pt"
        	></v:image>
        <![endif]-->
        ```

        -   `450px × 332px` → `337.5pt × 249pt` (approx)

    -   **Rounded rect with image fill (clickable)**
        ```html
        <!--[if mso]>
        	<v:roundrect
        		stroke="f"
        		arcsize="6%"
        		style="width:168.75pt; height:124.5pt"
        	>
        		<v:fill
        			type="frame"
        			src="https://…/image.jpg"
        			href="https://example.com/1"
        		/>
        		<w:anchorlock />
        	</v:roundrect>
        <![endif]-->
        ```
        -   Use `type="frame"` to preserve image aspect inside the frame
        -   Omit non-standard attributes (e.g., `sizes="…"`) — keep it to `type`, `src`, `color`, etc.

-   **Hybrid (fallback) pattern you should pair with VML**

    -   Always include **standard HTML** content as the default; VML inside **MSO conditionals** enhances Outlook only.
    -   Example button fallback (for non-Outlook clients):
        ```html
        <a
        	href="https://example.com"
        	style="display:inline-block; background:#546c49; color:#ffffff; text-decoration:none;
                  font-family:Arial, Helvetica, sans-serif; font-size:18px; line-height:20px;
                  padding:12px 24px; border-radius:16px;"
        >
        	BUTTON
        </a>
        ```
        -   Place the HTML fallback **outside** the `<!--[if mso]>…<![endif]-->` so everyone else sees it.

-   **General VML tips**

    -   Wrap all VML in `<!--[if mso]> … <![endif]-->`.
    -   Prefer **pt** for `width/height/strokeweight`; keep colors hex.
    -   If you need background images in containers, consider the classic VML background technique:
        -   `v:rect` with `v:fill type="frame" src="…"` and `mso-width-percent` / `mso-height-percent` tricks (advanced).
    -   VML can’t do `alt` text — ensure your **HTML fallback** includes a normal `<img>` with `alt`.

-   **Troubleshooting**
    -   **VML not rendering?** Check namespaces and conditional comments; ensure tags are properly closed.
    -   **Button text off-center?** Adjust `v:textbox inset` and text `line-height`.
    -   **Edges look jaggy?** Increase `strokeweight` slightly or reduce contrast; VML anti-aliasing is limited.
