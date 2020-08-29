# Responsive Web Design


### LEARNING OBJECTIVES

_After this lesson, you will be able to:_

- Describe what Responsive Design is 
- Explain the benefits of Mobile First design
-  Use CSS Media Queries to alter page layout and styling
- Define a function in an object
- Pass a function as a parameter

## What is responsive design? 

"Responsive Design" is the strategy of making a site that "responds" to the browser and device that it is being shown on... by looking awesome no matter what.

Or, the dryer Wikipedia definition:

"Responsive web design (RWD) is a web design approach aimed at crafting sites to provide an optimal viewing experience—easy reading and navigation with a minimum of resizing, panning, and scrolling—across a wide range of devices (from mobile phones to desktop computer monitors).""

#### More devices

Not that long ago, building a successful online presence meant just ensuring that your website worked correctly in all the major desktop browsers.

Fast forward to today, and the desktop computer is dying, more than 71% of the US population own a smartphone.

Here are some facts from [2020 Mobile vs. Desktop Usage Insights](https://techjury.net/blog/mobile-vs-desktop-usage/#gref)

- Over the course of one year, mobile users share increased by over 10%.
- Mobile vs desktop usage stats in 2020 reveal 50% B2B inquiries are made on mobile.
- Social media takes 25% of all digital media consumption and it is mainly accessed on mobile.
- 51% of the time spent online in the US is on mobile devices.
- Mobile market share worldwide is 52.1% compared to the desktop market share of 44.2%.
- 40% of people search only on a smartphone.
- More than half of all video views come from mobile devices.
- Mobile apps have higher engagement rates than mobile-optimized websites or desktop web viewing.


## Responsive Web Design

**Responsive Web Design**, not surprisingly, is designing a web page to respond to the size of the device's screen being used to view it.

Specifically, the most important criteria to respond to is the **width** of the device's screen.

Lastly, what specifically **responds**? Primarily, the overall layout of the page, but you can pretty much change anything on the page you want.  For example, I'm sure you've seen the menu links in a navigation bar disappear and be replaced with a "hamburger" icon before.  Take a look at the image at the top of this lesson too - notice how the number of columns changes?

Okay, now that you know what Responsive Design is, let's look at some real-world examples out there.

## Mobile First Design Philosophy

There are two approaches that can be followed:

1. Write the starting CSS for a large, desktop screen, then apply "new" CSS (using media queries) as the screen width decreases, or
2. Write the starting CSS for a mobile screen, then apply additional CSS as the width increases.

The experts tell us that it's better, to use a **mobile first** approach for the following reasons:

- Translating the design from mobile to desktop is easier than vice-versa, thus it should require less time to build the site.
- Mobile first encourages you to think about what content is the most important - and prioritize them.
- It's easier to detect performance related issues, such as the slow loading of large image files, on mobile devices and it's better to deal with performance issues early on.
- A design based on a small screen width, although not ideal, is usable on larger devices, however the reverse is often not the case.

## First Step to Enabling a Better Experience on Mobile

Unlike on desktop browsers that render pixel-by-pixel, mobile browsers actually render to a virtual **viewport**. This virtual viewport concept is what enables pinching to zoom in and out.

By default, mobile browsers scale down the content to fit it in the browser window, resulting in tiny text that's hard to read.

#### `<meta name="viewport" ...>` to the Rescue

The viewport `<meta name="viewport" ...>` enables us to inform the browser not to scale the page as seen above and instead, display the content based upon the physical number of pixels available - just like desktop browsers do.



Between the two images below can you guess which one is using the viewport tag? 

<img src="https://i.imgur.com/1d3F76a.jpg">

This viewport `meta` tag is so important, that VS Code has been adding it automatically in the HTML boilerplate.

The following should look familiar...



```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

### Testing Responsive Designs

#### Chrome Device Toolbar

DevTools comes with a great feature to easily view a web sites responsiveness using the `device toolbar`. 

<img src="https://i.imgur.com/DHYdzht.png" width=300/>

Once the toolbar is activated we will be able change the screen width using the sections just above the site or the slider bar to the right.

<img src="https://i.imgur.com/pdFgvi2.jpg" >

#### Am I Responsive

Another option is to use [ami.responsivedesign.is](https://i.imgur.com/pdFgvi2.jpg).  This will display a site in 4 different viewports.

<img src="https://i.imgur.com/R63nt7j.jpg" />

## Introducing Media Queries

Media queries are a CSS feature that lets you define properties and values at
different browser widths.

The media query can be composed of any number of media feature expressions and an optional media type, such as print, screen, or all.

Here's what a media query looks like in its simplest form:

```css
@media screen and (max-width: 500px) {
  width: 100%;
}
```

Let's break it down:

- `@media` is the start of the declaration. required.
- `screen` tells the browser to only use this on the screen. Another option is
  `print` for pdfs or printing out html pages. optional.
- `(max-width: 500px)` is one of the parameters you can specify. There are lots.
  This tells the screen to only apply this query when the screen width is BELOW
  500px.

> For reference:
> https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries

## Breakpoints

Breakpoints are just a set (usually 3-5) of viewport widths, that you use in
conjunction with media queries.

You want your website to react predictably - therefore you should decide when
you want your media queries to do their magic, and stick to that same set.

Here's what [bootstrap](https://getbootstrap.com/docs/4.1/layout/overview/), the
most popular CSS framework uses:

```css
/* Small devices (landscape phones, 576px and up) */
@media screen and (min-width: 576px) {
  ...;
}

/* Medium devices (tablets, 768px and up) */
@media screen and (min-width: 768px) {
  ...;
}

/* Large devices (desktops, 992px and up) */
@media screen and (min-width: 992px) {
  ...;
}

/* Extra large devices (large desktops, 1200px and up) */
@media screen and (min-width: 1200px) {
  ...;
}
```

You're not tied to using only these specific widths, but keep them for the sake
of this exercise.

> Related:
> [here's a really good article](https://medium.freecodecamp.org/the-100-correct-way-to-do-css-breakpoints-88d6a5ba1862)
> on how you should choose your breakpoints

## Our Design

We'll use these media queries and breakpoints together to make sure that our
website looks nice on all sized devices!

Let's make some changes to the starter code to make our site responsive.

The first thing we should do is get a sense of all the different components that
we want to affect using media queries.

#### Desktop Version
Below is a desktop version of a build that you might have already done in class.

<img src="https://i.imgur.com/qG9wv1U.png" width=700/>

#### Mobile and Tablet Versions
And here is the same web site with media queries enabled for mobile and desktop.

<img src="https://i.imgur.com/sJ3w9bS.png" />


### Our First Media Query

```css
@media screen and (max-width: 576px) {
  .small-100 {
    width: 100%;
  }
}
```


You can also do this in reverse - hiding stuff on large screens and only showing
on mobile. Think about the hamburger menu that appears on mobile navbars.

## Thinking responsively

When planning your site, don't think about a piece of paper on a desk with stuff
drawn on it. That's a fixed layout! Instead, think in components and think about
how those components will look on different devices.

Start from the mobile layout and scale up when designing your page. Most CSS
frameworks are mobile-first, mobile is a huge portion of web traffic, and it's
easier to scale up and add items than cram stuff into a small space.

It's 2019. We don't build non-responsive websites anymore!



## Resources

- A list of device viewport sizes: http://viewportsizes.com/
- [Solution branch for the starter code](https://git.generalassemb.ly/dc-wdi-fundamentals/responsive-web-design-starter-code/tree/solution-responsive)
  - can also run `git checkout solution-responsive` in the repo we forked and
    clone earlier.
