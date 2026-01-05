# README-4

## Purpose

Update the form look and feel using Cascading Style Sheets.

## Cascading Style Sheets

CSS 3.0 is a declarative language that defines rules about how elements of a document (and the document itself) appear:

- Color: Background, border, font.
- Size: Elements can be sized to pixels, percentage of viewable window size, etc.
- Shape: Elements are boxes (quadrilateral) by default, but can be coerced into triangles, ellipse shapes, etc.
- Position: Elements are considered boxes that contain content like text. CSS can control the box position on the screen, as well as the position of the content within a box.

The more you know about CSS, the more effective the form style will be.

## Style For Accessibility

CSS is great for managing web page accessibility concerns including:

- Color contrasts to make text easy to read.
- Using color to guide the user to specific parts of the page such as buttons with specific behaviors.
- Highlighting active items and dimming inactive items.

## What This Module Covers

This training module is _not comprehensive_:

- Introduction to simple use-cases for CSS in a Winlink Form.
- Benefits and drawbacks of inline CSS, page CSS, and referenced CSS.

## What to Expect

If you have none or very little CSS experience:

- Simple, effective CSS is fairly simple.
- Can quickly become complex when defining responsive web pages (but is worth the effort).
- Will require additional outside help to get going, including training courses (free and/or paid) available online and in-person.
- Might be helpful to pair-up with an person experienced with CSS to help turn ideas into CSS code.

If you are an experienced programmer:

- This content might appear to be obvious and oversimplified.
- Can pick-up the concepts and get going right away enhancing a Winlink Form.

The idea is to introduce the capabilities so you can pick it up and run with it.

## Employing CSS

There are 3 ways to employ CSS on a web document:

1. Create a file and name it 'style.css'. Add a stylesheet reference in the header of the HTML, pointing to the file.
2. Define CSS rules within a `<style>` element within the web document.
3. Define CSS rules in-line with the HTML element they will apply to.

There is a fourth: Some compbination of 1, 2, and/or 3.

Benefits and Drawbacks of file-based, style element rules, and in-line styles:

- File-based is simpler to manage and maintain collaboratively. Styles can be applied to the entire document as well as individual elements, or groups of elements.
- Using the `<style>` tag mixes HTML and CSS together into the same file, making it more difficult to maintain by adding lots of clutter. However, it is easier to deliver a single-file solution (HTML + CSS + Javascript in one file) than to deal with accurate distribution to users.
- In-line styles are great for on-off rule setting, but are relatively static, and even more difficult to maintain because it is sprinkles throughout the code. This is the least effective and most difficult way to implement and maintain CSS.

## How CSS Works

Recall: HTML provides the Layout for the content of a web page.

CSS defines properties like color and width so the page and HTML elements know what size and color they are.

Inheritance:

- CSS applies to the web page document and the HTML elements within it.
- CSS properties applied to a parent element may also apply to that elements children.

Special CSS functions allow selecting what elements in a hierarchy have styles applied to them.

As an example, a font family and background color are defined and applied to the `body` element:

```css
body {
    font-family: 'Segoe UI', Tahoma, Verdana, sans-serif;
    background: #3399FF;
}
```

HTML elements within the `<body>` element will inherit these CSS properties:

```html
<!DOCTYPE html>
<html lang="en">
    <head></head>
    <body>
        <h1>Document Heading</h2>
    </body>
</html>
```

This is the "cascading" part of CSS. Take advantage of it when setting styles to your web page.

## Helpful Tools

Browser Developer Tools:

- Modern browsers have this built-in.
- Menu > More Tools > Developer Tools.
- CTRL + SHIFT + I
- `Inspector` or `Elements` Tab: Interact with HTML, CSS, and "events" that make up the structure, style, and behavior (respectively) of the web page.

When a style doesn't seem to be applied, or doesn't do what you thought it should, start by looking at the `Elements` tab, click on the element with the problem, and review the `Styles` sub-tab (next to `Computed` and `Layout`).

### Developer Tools Inspector/Elements Tool

1. Launch your web page and then open Developer Tools.
2. Right-click on an element (like a button) on your web page and select `Inspect`

HTML is displayed on the left (the document Layout), and CSS is displayed on the right (the style application tree).

### Navigating The Inspector

1. The selected (inspect) element should be highlighted (selected) in the Developer Tools window.
2. The `Styles` tab (on the right) shows the CSS rules that are applied to that element.

Note the following style application denotations:

- Top subsection: `element.style`: Style properties applied _directly_ to the selected element.
- Next subsection: Rules applied and the line of CSS where it is applied from.
- Next: "user agent" style rules applied to the selected element.
- Scroll down to the bottom. The _box_ display tells you how the selected element is definedd and formatted based on the HTML and the CSS application. The center blue box is the content area.

`user agent` styling: This is the default CSS that browsers apply to the document by default. Without defaults, you would be forced to style every single element on your web page. These `user agent` styles are overridden by the CSS that you write.

## Targeting HTML Elements

Just like Javascript, CSS can target HTML elements individually, as a group, or through _inheritance_ (the "cascading" part of CSS).

Target elements of type:

```css
section {
    display: flex;
    justify-content: flex-end;
    padding: .2em;
}
```

```html
<section>
    <input type="button" name="SaveButton" id="saveButton" value="Save Data"></input>
</section>
```

Target elements with some class:

```css
.input-container {
    width: 100%;
    margin: auto;
    text-align: center;
    padding: .2em;
}
```

```html
<div class="input-container">
    <label for="mycall">Enter your callsign:</label>
    <input type="text" name="mycall" id="myCallsign" />
</div>
```

Target one specific element by unique ID:

```css
#submit-container {
    display: flex;
    justify-content: flex-end;
    padding: .2em;
}
```

```html
<div id="submit-container">
    <input type="submit" name="Submit" value="Submit" />
</div>
```

## Common CSS Properties

`font-family`: Pick easy to read, well-spaced fonts like Segoe UI, Tahoma, Verdana, and non-serif fonts.

`font-size`: 16px is a common default, and 18px is a pretty good setting to help improve readability. The downside is if you assign a default font-size, adjusting font-size of other elements requires a little more work. In any case, larger or smaller screens should probably use slightly larger or smaller values - see [Responsive Design](#responsive-design) section below for more information.

`background`: Assign a color to the background of the element(s). Best supported color definitions are in hexadecimal (0-F) formatted and assigned like `#rrggbb` (see next subsection).

`width` and `height`: Assign element size using pixels (px), percentage %, and other units (there are many to choose from).

`margin`, `border`, and `padding`:

- Padding defines the area surrounding the content inside of the element. Use this to control the space between the content and the inside "walls" of the element that contains the content.
- Border defines the style and size of the border surrounding the elements Padding.
- Margin defines the area surrounding the padding and border. Use this to help separate elements.

`display` Defines how the element will be displayed:

- Block: The default for layout-oriented elements that self-aligned vertically.
- Inline: The default for most content-oriented elements that self-align horizontally.
- None: Rendering does not display the element (but it is still there).
- Inline-block, flex, and grid: 3 others that can be explored.

## Hex Color Hints

- Black: `#000000`
- White: `#FFFFFF`
- Red: `#FF0000`
- Green: `#00FF00`
- Blue: `#0000FF`
- Purple: `#FF00FF`
- Yellow: `#AAAA00`
- Aqua: `#00FFFF`
- Light Blue: `#1199FF`
- Orange: `#FF9911`

## Responsive Design

Make web pages render well on varying screen sizes and resolutions, maintaining usability and readability.

This is a very large, advanced topic. There are benefits from knowing a few basics, followed by some studying to learn the advanced techniques to make an _awesome_ web page.

### Media Queries

CSS will apply rules based on what the browser document says the resolution and screen dimensions are:

```css
body {
    font-size: 18px;
}

@media screen and (width < 650px) {
    label,
    input,
    button {
        font-size: 0.7em;
    }

    form {
        max-width: 100%;
        padding: 0.4em;
        background: linear-gradient(#11ccee, #11aaff);
        border-radius: 20px;
    }
}

@media screen and (width >= 650px) {
    label,
    input,
    button {
        font-size: 1em;
    }

    form {
        max-width: 650px;
        padding: 0.6em;
        background: linear-gradient(#11ccee, #11aaff);
        border-radius: 20px;
    }
}
```

The `@media` statement tells CSS to only apply the rules when the parameters are met:

- `screen`: The Screen object is available. This could also be an evaluation like `screen.pixelDepth < 8`, meaning fewer colors are available so use a grayscale instead of full color spectrum.
- `width`: The width of Screen in pixels. The condition could be `height` instead or a combination of the two.

Keep the number of `@media` conditions to a minimum to keep the benefit of the effort very high.

### Toggle Device Toolbar

Developer Tools has a little button named 'Toggle Device Toolbar' (or similar - in Chrome it is in the upper-left hand corner, just to the left of the 'Elements' tab).

Clicking this button alters the 'screen' property of the browser display window. Doing so now will probably load an iPhone view with dimensions that represent a mobile device.

There is a "Dimensions" drop-down in the upper-left area of the browser window that allows selection of many common mobile device screen sizes.

There is a "Rotate" button in the upper-right area of the browser window that allows rotating the screen.

Advice:

- Determine a few key devices/sizes that you want to support that most of your users are likely to be using (don't go crazy customizing CSS for 15 different phones and tablets).
- Use these to help determine when you've found reasonably responsive settings.

### Responsive Design Challenge

1. Copy `styled-form.html` from module 2 and name it `responsive-form.html` (or something that makes sense to you).
2. Copy the above CSS from into a `<style>` element within the `<body>` of the html and save the changes.
3. Copy the full path to the html file you just edited and paste it into your favorite browser's URL bar and press Go/Enter key.
4. Open Developer Tools and inspect the HTML and CSS.
5. Click "Toggle Device Toolbar" (Chrome) to enable the mobile device view and try different Dimension settings (including rotation) to see how the form responds.
6. Update the code in `responsive-form.html` by replacing "Form Fields Start" example code with "Form Fields Responsive" example code, save the changes, and refresh the browser window.
7. Try different Dimension settings again and see how the page respondes.

Form Fields Start:

```html
<label for="mycall">Enter your callsign:</label>
<input type="text" name="mycall" />
<label for="tocall">Enter recipients callsign:</label>
<input type="text" name="tocall" />
```

Form Fields Responsive:

```html
<div>
    <label for="mycall">Enter your callsign:</label>
    <input type="text" name="mycall" />
</div>
<div>
    <label for="tocall">Enter recipients callsign:</label>
    <input type="text" name="tocall" />
</div>
```

This is just an example of the power of responsive design using just HTML and CSS.

Adjusting [Media Queries](#media-queries) will help to refine exact bahavior based on screen sizes your users are most likely to be using. Remember to keep the number of cutoff values to 2 or 3 to keep for over complicating the code.

## Install

Put files into Winlink Express `Global Folders\Templates` directory:

- `4-form-style\tagged-styledform-template.txt`
- `4-form-style\styled-form.html`

Remember: You can move the javascript to a separate file if you wish, but remember to:

1. Store it to the same directory as these files (for simplicity).
2. Add a `<script ref="">` element just before the end of body `</body>` element tag.

## Use

1. Open Winlink Express.
2. Click 'New Message'
3. Click 'Select Template'
4. Click `tagged-styledform-template.txt` in the Global Templates directory.
5. Click the 'Select' button and the default browser will launch, displaying the `styled-form.html` form.
6. Complete the form by adding values to the text boxes.
7. Click Save button to download the form data to a file.
8. Click Submit button and the form data is transferred to the new message window.

## Resources

- TemplateHelp.txt
- Insertion Tags.txt
- [Responsive Web Design](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/CSS_layout/Responsive_Design)
- [Media Query Fundamentals](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/CSS_layout/Media_queries)
