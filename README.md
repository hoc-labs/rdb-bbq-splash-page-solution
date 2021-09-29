# BBQ Splash Page

We're going to work on building the HTML/CSS for this splash page. 

![](https://raw.githubusercontent.com/hoc-labs/images/main/rdb-bbq-img1.png)

There are lots of new concepts in this project:
* background images
* forms
* gradients

As well as more flexbox and responsive design work.

### Big Picture Planning
Before continuing, think about how you would build the markup for this page. It's important to start a project by analyzing the overall layout before diving in.

#### Design Issues of Interest
The first thing to notice is that the version on the left has two columns, whereas the version on the right has the two sections stacked. We can use flexbox for that.

Another thing is that the text on the left is all grouped together, whereas on the right, it is spread out. From a design perspective, this makes sense, because on a larger screen, that bottom text would get lost if it's at the bottom. Whereas on the right, the reader moves easily from the top to the bottom text.

### Layout Structure
![](https://raw.githubusercontent.com/hoc-labs/images/main/rdb-bbq-img2.png)

### Design Specification

If you like to look at the Adobe XD files, [here's the link](https://xd.adobe.com/spec/3bcaad42-bd8a-415e-6274-08b282cfb769-4dfb/).

And here's the condensed version.

![](https://raw.githubusercontent.com/hoc-labs/images/main/rdb-bbq-img3.png)


### Adding the HTML Markup

Here is one way for the markup to be structured. This project is more about the some special techniques with CSS so the markup is pretty basic. The `<form>` is also not there yet.

### - Headings

Notice the use of `<p>` elements for the text under the `<h1>` and the `<h2>`. We us a `<p>` instead of say an `<h2>` under the `<h1>` ,because each section should have a single heading, and you choose the correct heading for the sub-sections. Within a section, you should use `<p>` for the sub-title text.


```html
  <!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link href="https://fonts.googleapis.com/css?family=Source+Sans+Pro:300,400,900&display=swap" rel="stylesheet">
  <title>My Page</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="intro">
      <h1>Learn how to make the best BBQ ribs in town</h1>
      <p class="subtitle">Join us for this live webinar</p>
      <p class="top-text">Mouthwateringly delicious</p>
  </div>
  
  <div class="main-content">
      <h2>Become a BBQ master! </h2>
      <p class="subtitle">Register Today</p>
      <p>BBQ isn't just standing in front of your grill with it on full blast and hoping for the best. It's an art! One way to speed up the process is to learn from the best. You can do just that by signing up for this free webinar!</p>
      <!-- form will go here -->
      <p class="fine-print">We'll never share your information without your permission</p>
  </div>
</body>
</html>
```
### - Child Element Ordering

The child elements in each of the div containers are not in the order that they appear on the specification. A technique that some web developers use is to order the elements according to priority rather than position.  That way, if for some reason the CSS does not load correctly, the content will be displayed in priority order. We can use flexbox to order the elements independent of how they are ordered within the markup.

Also, the font for this project has already been included, and notice that includes the 300, 400, and 900 weights.

### Styling

What's the first selector we should start with? It is the `<body>` element.

#### `<body>` styling
* We always want to get rid of the margin.
* Here's where we set the global font, font size and text color.

The color choice is meant to soften the text from the pure black.


#### `<h1>` styling
Next we'll set up the style for the `<h1>`. We'll postpone setting the text color to white, until after we get the background image setup. Otherwise we won't be able to see the text.

* font-size
* font-weight

#### center content
Next, center the content. You'll notice that everything in this design is centered. So think about where the best place to add the CSS to center the elements is.


#### `<h2>` styling
Next, style the `<h2>` element. It just requires a font-size.

#### style the `<p>` following the `<h1>`
* text color
* font-weight
* font-size
* uppercase


#### `<strong>` styling

We can wrap the text within the `<h1>` element with a `<strong>` element, but if you preview the page, you'll see that it isn't very dark. The reason for this is the browser looks at the current font-weight on the `<h1>`, which is 300, and move up to the next available font, which is 400.

So, we need to explicitly set the font-weight to 900 to get the desired darkness.

```html
 <div class="intro">
      <h1>Learn how to make <strong>the best BBQ ribs</strong> in town</h1>
      <p class="subtitle">Join us for this live webinar</p>
      <p class="top-text">Mouthwateringly delicious</p>
  </div>
  ```

```css
strong {
  font-weight: 900;
}
```

#### top text styling

* font-size
* font-weight
* color
* uppercase

#### fine-print styling
* font-size
* letter-spacing

Here's what the page should look like at this point.

![](https://raw.githubusercontent.com/hoc-labs/images/main/rdb-bbq-img4.png)

Here's the corresponding CSS:
```css
body {
    margin: 0;
    font-family: 'Source Sans Pro', sans-serif; 
    font-size: 1rem;
    color: #404040;
    text-align: center;
}

h1 {
    font-size: 2.25rem;
    font-weight: 300;
}

.intro .subtitle {
    color: #F18119;
    font-weight: 900;
    font-size: 1.3125rem;
}

h2 {
    font-size: 1.3125rem;
}

.main-content .subtitle {
    color: #F18119;
    font-weight: 900;
    font-size: 1rem;
    text-transform: uppercase;
}

.top-text {
    font-size: 0.625rem;
    font-weight: 900;
    color: #F18119;
    text-transform: uppercase;
}

strong { font-weight: 900; }

.fine-print {
    font-size: 0.625rem;
    letter-spacing: 1px;
}
```

### Styling the Intro Section

#### Background Images

* set the background-image property on the .intro selector. 
* set the text color to white on the `<h1>` so we can see it.

#### Padding

We need some space around the text in the intro section, but padding on all sides won't be a good solution in this case because we want to push the one piece of content up against the upper edge.

For now, add some padding on the other sides only.


Here's what the page should look like with the changes:

![](https://raw.githubusercontent.com/hoc-labs/images/main/rdb-bbq-img5.png)


#### Default background-color

One issue we want to address is to supply a background-color in addition to the background-image. This is necessary in case the connection is really slow and the image takes a long time to load. Because the text is white, it won't show up if the background image isn't there.

So it is best-practice to set the background color to something that would look good if the image doesn't load.

Once you have made the change below, try experimenting with the various states by commenting out the background-image and background-color to see how you can't see the text in this case, and then just commenting out the background-image to see the fallback.

```css
.intro {
    background-color: #404040;
    background-image: url(images/dark-ribs.jpg);
    padding: 0 .25em 1em;
}
```

#### Changing the Order of Flex Elements

The order of the elements in the HTML are different than we want them displayed on the screen. Use flexbox's order property to set the correct order.

Try previewing the page with the display:flex commented in and then out. You will notice that things change a little bit. With display:flex turned on, the white-space on the top disappears. 

This is because when flex is turned on, margins no longer collapse.

```css
   
.intro {
    background-image: url(images/dark-ribs.jpg);
    background-color: #404040;
    padding: 0 .25em 1em;
    /* using flex to re-order the elements */
    display: flex;
    flex-direction: column;
}

.top-text {
    font-size: 0.625rem;
    color: #F18119;
    font-weight: 900;
    text-transform: uppercase;
    /* make this appear at the top */
    order: -1;
}
```

#### main content styling

Here we just need to work on getting the spacing right, and make sure the elements that need to be in uppercase are styled.

### Adding Media Queries for Responsiveness

One way to determine the breakpoint for your media query is to look at the text and decide when it is getting too long to read easily.

This is why magazines always have columns of text in an article. It makes it easier to read.

For this project, a breakpoint of around 500px seems about right.

The tasks that we need to fix for the full size:
* create a two column layout
* increase the font-size where specified.
* set background-size and background-position to make the center of teh image always show as the screen size changes.

### Viewport Units

Viewport units are a responsive unit. It is a percentage based on a width/height of the browser window.

There are two viewport units that we're going to focus on:
* vh - viewport height
* vw - viewport width

As we have seen, setting a hard-coded height can be problematic. It can cause the content to overflow down into the next element below it.

Setting the height to a percentage also doesn't work, unless the parent has a hard-coded height.

The viewport height, or vh, property, allows you to set the percentage of the browsers visible content that the element should take up.

These are useful when we want to set the height of a section on the page to a percentage of the visible page in the browser.

This is very common when you have a hero section, like our BBQ splash page, that you want to always stay visible.

For example, we could set do the following:

```css
.intro {
  height: 100vh;
}
```

and this would make the intro section always take up 100% of the viewport.

#### Using vh units

Right now in our site when we shrink the widht/height of the browser window, some of the content scrolls out of view.

To fix this, we can set the height to 100vh. We only want to do this when the page is in the full-size view, not the media query for the smaller size, since then it will stack and it makes sense for some of it to be out of view and require scrolling down the page.

Start with using height:100vh and see how it looks. The section is correctly filling 100% of the height, but the problem is that the text content cannot fit in that height, so it is overflowing and you end up with white space below the image and scrolling.

If we use min-height instead of height, this will fix this issue. It will force scrolling, if the content extends beyond 100%, but the background image will span the required height.

As a general rule, it's better to use min-height, instead of height, when using viewport units, just in case a situation like this arises.

```css
    .intro,
    .main-content {
        width: 50%;
        min-height: 100vh;
    }
  ```
  
### Box-sizing

If you notice, we still get some vertical scrolling on our page. The 
padding on the intro and main content is causing this. When the browser is calculating the height of the elements, by default it is just using the height of the content within the element. It is not including the padding or border.

In most situations, this is not what we want. It's sort of like the margin on the body. We set it to 0 in most of our projects.

The property that we want to use here is box-sizing. By default, it is set to content-box. But we can set it to border-box, which will include the padding and border in the width and height calculations.

So add this to the top of your stylesheet and now preview your page. The scrolling issue should be fixed. This is a style that web developers almost always set in all of their projects.

```css
* {
    box-sizing: border-box;
}
```

### Distributing the content vertically
* on the right you should be able to use flexbox to center the content.
* on the left, we need to remove the margin that we initially put on the `<h1>` element and then use flexbox justify-content to spread them out.
* use min-height with a value in viewport units so that the intro never gets too small.


### Forms

Using the form-sample.html as a guide, add the simple form to the page.
* remember to add a border-radius to the button.

### Gradients

Using the gradient-sample.html as a guide, add a gradient to the submit button on the form.

We want to also add a gradient to the text on top. To do this we want to first add a border to the top.
* add border to the top
* remove the space between the border and the top edge
* add some padding between the content and the border.
* use the border-image property to set the gradient.
  * border-image: linear-gradient(to left, #ff713b, #ffa51d) 1;
  * you need to add the 1 at the end to tell it how many slices (something necessary because it is usually an image).







