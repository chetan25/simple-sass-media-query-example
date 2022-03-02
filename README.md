# Simple Sass Example with Media Queries

- This repo contains a simple example showing how we can implement media Queries with CSS and Sass.
- The project has 3 folders for stylesheets
  - `css` - for basic css styles
  - `scss-mixin` - styles with sass, mixin for media queries and partials for variables.
  - `scss-mixn-partails` - This is build on top of `scss-mixin`, but we have created partials for each breakpoint.

**_ Note - we have compiled the sass with VS Code plugin (Live Sass), and have set the output directory be dist _**

- If you prefer to compile the css to different folder, just change the path in the html file.

## Media Queries

#### How to use it in Css

CSS media queries can be inserted in your HTML pages in the following ways:

- Inserted into a <link> element which refers to a CSS style sheet.
- This example shows how to add media queries to a link element. Only if the conditions in the media query is met is the CSS file applied to the HTML document.

  ```html
  <link
    rel="stylesheet"
    href="mycss.css"
    media="only screen and (max-width: 1200px)"
  />
  ```

- Inserted before an @import CSS instruction in CSS style sheet.
- This example shows how to import a CSS style sheet from within another CSS style sheet. You can append a media query to the @import instruction. Only if the conditions in the media query are met is the CSS file imported and applied.

```css
@import url("my-other-css.css") only screen and (max-width: 1200px);
@import url(myfile.css) screen;
@import url(myfile-print.css) print;

@import url(myfile.css) screen and (aspect-ratio: 4/3);
```

- Inserted inside a CSS style sheet.
  An example is shown below for each of these methods:

```css
@media only screen and (max-width: 1200px) {
  /* css rules */
}
```

### Media Query Syntax

- [logic] [media] [and (condition)] [and (condition)]

- only The value only means that this media query only matches a certain media type (the next parameter in the media query).
- not The value not means that this media query matches all other than a certain media type (the next parameter in the media query).

- screen Matches all computer screens. Both on desktop computers, laptops, tablets, smart phones and TVs. (screen is the default.)
- projection Matches projection devices (projectors used in meeting rooms etc.).
- print Matches when a user clicks "print" for the page.

- width Specifies the width of the browser window this media query matches.
- min-width Specifies the minimum browser window width this media query matches.
- max-width Specifies the maximum browser window width this media query matches.

```html
<style>
  @media only screen and (max-width: 600px) {
    /* CSS rules for browser widths equal to or less than 600px */
    body {
      background-color: #ffffff;
    }
  }
  @media only screen and (min-width: 601px) and (max-width: 1200px) {
    /* CSS rules for browser widths from 601px to 1200 px */
    body {
      background-color: #ff0000;
    }
  }
  @media only screen and (min-width: 1201px) {
    /* CSS rules for browser widths from 1201px and up */
    body {
      background-color: #0000ff;
    }
  }
</style>
```

#### Media Queries in SCSS

- There are two ways to apply a certain rule set to a element based on media query in scss
- First way we can do it similar to what we do in css file

```scss
/* Using SCSS variables to store breakpoints */
$breakpoint-tablet: 768px;

// default rule set
body {
  color: orange;
}

@media (min-width: $breakpoint-tablet) {
  body {
    color: red;
  }
}
```

- Second way is we define the media query inside the element itself

```scss
/* Using SCSS variables to store breakpoints */
$breakpoint-tablet: 768px;
body {
  // default rule set
  color: orange;
  @media (min-width: $breakpoint-tablet) {
    color: red;
  }
}
```

- More advance way would be using `mixin` which is shown in the examples.

##### Pixel usage Images

- We tend to think that in mobile devices, the loaded images should be smaller since the devices’ width is smaller. But that isn’t always true.
- CSS Resolution and Screen Resolution: The CSS resolution is used for measurements in our website, and the Screen Resolution is the actual number of pixels on the screen.

Example:
Samsung Galaxy S10 Resolutions:
Device Resolution — 1440px by 3040px
CSS Resolution — 360px by 760px
Density Display — 4x (4 times for every pixel)

#### Raster and Vector Images

##### Raster Images

- Raster graphics are bitmaps.
- A bitmap is a grid of individual pixels that collectively compose an image.
- Raster graphics render images as a collection of countless tiny squares.
- Each square, or pixel, is coded in a specific hue or shade. Individually, these pixels are worthless.
- If you make a raster larger, it will become “pixelated” and lose quality.
- The resolution of a raster image is defined by dpi (dot per inch).
- .jpg ,.bmp , .tiff, .gif, .png
- are used primarily for graphical work: photography, print, website images, digital artwork.
- raster images are pixel-based, they suffer a malady called image degradation.

###### Vector image

- A vector image is scaleable.
- That means you can change the size to as large or small as you want and the image will remain the same quality. That’s because it’s mathematical.
- If you draw a square of 1cm by 1cm and you scale it by 100 you will have a box that is 100cm by 100cm and it will look exactly the same.
- No quality will be lost. You are simply telling the computer to draw a line between different points.
- logo design
