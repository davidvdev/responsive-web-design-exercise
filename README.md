
---

Title: Introduction to Responsive Design<br>
Author: Joe Keohan<br>
Duration: 120min+<br>
Competencies: HTML, CSS Basics, <br>
Prerequisites: Flexbox, CSS Grid<br>

---

# Responsive Web Design




### LEARNING OBJECTIVES

_After this lesson, you will be able to:_

- Describe the concepts of **Responsive Design** 
- Explain the benefits of **Mobile First** design
- Use **CSS Media Queries** to implement a responsive design layout


## Responsive Web Design

**Responsive Web Design** is designing a web page to respond to the size of a specific device viewport. Specifically, the most important criteria to respond to is the **width** of the device's screen.  

For example, I'm sure you've seen the menu links in a navigation bar disappear and be replaced with a **hamburger** icon before.  

**Facts You Should Know**

Here are some facts from: [2020 Mobile vs. Desktop Usage Insights](https://techjury.net/blog/mobile-vs-desktop-usage/#gref)

- Over the course of one year, mobile users share increased by over 10%.
- Social media takes 25% of all digital media consumption and it is mainly accessed on mobile.
- 51% of the time spent online in the US is on mobile devices.
- Mobile market share worldwide is 52.1% compared to the desktop market share of 44.2%.
- 40% of people search only on a smartphone.
- More than half of all video views come from mobile devices.



## Mobile First Design Philosophy

There are two approaches that can be followed:

- Begin designing for a desktop screen, then apply additional CSS as the screen width **decreases**

**OR**

- Begin designing for a mobile screen, then apply additional CSS as the width **increases**.

Regardless of which approach you take you still must incorporate some method to determine when the viewport width has changed and then respond accordingly. 

### Mobile First Approach Benefits

The experts tell us that it's better, to use a **mobile first** approach for the following reasons:

- Mobile first encourages you to think about what content is the most important - and prioritize them.
- Translating the design from mobile to desktop is easier than vice-versa, thus it should require less time to build the site.
- A design based on a small screen width, although not ideal, is usable on larger devices, however the reverse is often not the case.

## First Step to Enabling a Better Experience on Mobile

Unlike on desktop browsers that render pixel-by-pixel, mobile browsers actually render to a virtual **viewport**. This virtual viewport concept is what enables pinching to zoom in and out.

By default, mobile browsers scale down the content to fit it in the browser window, resulting in tiny text that's hard to read.

#### The Viewport Meta Tag 

The viewport meta tag **<meta name="viewport" ...>** enables us to inform the browser not to scale the page and display the content based upon the physical number of pixels available - just like desktop browsers do.



Between the two images below can you guess which one is using the viewport tag? 

<p align="center">
  <img src="https://i.imgur.com/1d3F76a.jpg" width=600>
</p>

This viewport **meta** tag is so important, that all editors have been adding it automatically as part of the HTML boilerplate.

The following should look familiar...



```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

### Testing Responsive Designs

#### Chrome Device Toolbar

DevTools comes with a great feature to easily view a web sites responsiveness using the **device toolbar**.  

<img src="https://i.imgur.com/DHYdzht.png" width=300/>

Once the toolbar is activated we will be able change the screen width using the sections just above the site (highlighted in red below) or the slider bar to the right.

<img src="https://i.imgur.com/pdFgvi2.jpg" >



#### Am I Responsive

Another option is to use [ami.responsivedesign.is](http://ami.responsivedesign.is/).  This will display a site in 4 different viewports.  

<img src="https://i.imgur.com/R63nt7j.jpg" />

<hr>

#### <g-emoji class="g-emoji" alias="alarm_clock" fallback-src="https://github.githubassets.com/images/icons/emoji/unicode/23f0.png">⏰</g-emoji> Activity - 5min

- Let's take a moment to see the effect of removing the **viewport** tag for a site
- Open [http://seir-1207-responsive.surge.sh](http://seir-1207-responsive.surge.sh) 
- Use the **Device Toolbar** to see what it looks like in **Desktop**, **Tablet** and **Mobile**
- The instructor will now comment out the viewport tag and push those changes
- Refresh the page and see if anything has changed
-Use **Device Toolbar** to see what it looks like in **Desktop**, **Tablet** and **Mobile**

:question: - What part(s) of the layout have changed?

<hr>

## Introducing Media Queries

Media queries are a CSS feature that lets you set CSS properties and values at different browser widths.

The media query can be composed of any number of media feature expressions and an optional media type, such as **print, screen, or all**.

Here's what a media query looks like in its simplest form:

```css
@media (max-width: 500px) {
  p { 
   color: red;
  }
}
```

And now one that specifically specifies this is for viewable screens

```css
@media screen and (max-width: 500px) {
  p { 
   color: red;
  }
}
```

And yet another one for when the user prints the page

```css
@media print and (max-width: 500px) {
  p { 
   color: red;
  }
}
```




Let's break it down:

- `@media` is the start of the declaration. required.
- `screen` tells the browser to only use this on the screen. The othe r option is
  `print` for printing out html pages.
- `(max-width: 500px)` is one of the parameters you can specify. 
  This tells the screen to only apply this query when the screen width is UP TO 500px but not beyond that size. 
- `p { color: red;}` is the element we are targeting

#### Additional Settings

Besides `max-width` there is also `min-width` and both an be used together in the same query. 

| Property       | What's It Do?                           | Examples                                  |
| --------------- | --------------------------------------- | ----------------------------------------- |
| max-width         | <= max-width                 | @media and (max-width: 600px)                                  |
| min-width | >= min-width| @media and (min-width: 600px)                        |
| max-width and min-width | between those ranges only               | @media only screen and (max-width: 600px) and (min-width: 400px)  |

<hr>

#### <g-emoji class="g-emoji" alias="alarm_clock" fallback-src="https://github.githubassets.com/images/icons/emoji/unicode/23f0.png">⏰</g-emoji> Activity - 5min

- Take a moment to examine the following [Mars site](https://0wqnv.csb.app/) in DevTools
- Make use of the **Device Toolbar** to see what it looks like in **Desktop**, **Tablet** and **Mobile**
- Inspect the **.container header .header-nav-area #nav_container** element 
- Now examine the css and look for a media query as you change from in **Desktop** or **Tablet** to **Mobile**


Add your findings to the slack thread created by the instructor.

<!-- INLINE STYLES -->
<!-- https://wpixk.csb.app/ -->

<!-- REACT SOCKS -->
<!-- https://xg8z2.csb.app/ -->

**Side Note**

That site was one attempt at rebuilding the official mars.nasa.gov site and using the experience to write the following medium article: [3 Ways To Implement Responsive Design In Your React App](https://medium.com/@jkeohan/3-ways-to-implement-responsive-design-in-your-react-app-bcb6ee7eb424)

It was developed further to include additional responsive design features prompting yet another article [React Responsive Slider](https://itnext.io/react-responsive-slider-2ed4b07867b3) and is currently at this stage in development: [Mars Responsive Slider](https://02nz9.csb.app/)

<hr>

## Breakpoints

Breakpoints are just a set of viewport widths (usually 3-5) , that you use in
conjunction with media queries.

You want your website to react predictably - therefore you should decide when
you want your media queries to do their magic, and stick to that same set.

Here's what [bootstrap](https://getbootstrap.com/docs/4.1/layout/overview/), the
most popular CSS framework uses as its breakpoints:

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


## Our Design

We'll use these media queries and breakpoints together to apply a responsive design to our site. 

The first thing we should do is get a sense of all the different components that
we want to affect using media queries.

#### Desktop Version
This is the desktop version of the site.

<img src="https://i.imgur.com/qG9wv1U.png" />

#### Mobile and Tablet Versions
And here is the same web site with media queries enabled for mobile and tablet.

<img src="https://i.imgur.com/sJ3w9bS.png" />



#### Live Site

Here is a [deployed version](http://seir-responsive-design.surge.sh/) of the site. Let's take a moment to test the site out using DevTools `device toolbar` and see the responsive design in action. 

<hr>

#### <g-emoji class="g-emoji" alias="alarm_clock" fallback-src="https://github.githubassets.com/images/icons/emoji/unicode/23f0.png">⏰</g-emoji> Activity - 5min

- Take a moment to examine the deployed site in DevTools
- Make use of the **Device Toolbar** to see what it looks like in **Tablet** and **Mobil**
- Inspect a few elements and see if you can discover a few media queries

When asked slack your response in a thread created by the instructor

<hr>

### Getting Started

#### Starter-Code Directory

- Navigate to the directory that contains the starter code
- Inside we will find the following:
  - `index.html` - it is already set up for you 
  - `style-main.css` - a little bit of css to get us started - it is already set up for you - 
  - `style-grid.css` - this contains all our initial css grid setup
  - `responsive.css` - this is where we will include our css

In the HTML we should see all the css files linked in the following order:

```html
  <link rel="stylesheet" href="style-main.css" type="text/css" media="all" />
  <link rel="stylesheet" href="style-grid.css" type="text/css" media="all" />
  <!-- RESPONSIVE CSS HERE -->
  <link rel="stylesheet" href="responsive.css" type="text/css" media="all" />
```

**Live Server**

Open **index.html** in **Live Server** and were ready to start coding.  

### Our First Media Query

Since the design is already setup for Desktop we will need to work our way backwards and will start with Tablet.  

**NOTE:** For the record you should always start with **MOBILE FIRST** so keep that in mind when your working through any additional layouts for labs/hw or even more importantly your unit projects.


**Tablet @ 768px**

Let's first add a media query that targets tablet devices. 
```css
@media screen and (max-width: 768px) {
 
}
```

**Section #1**

Now let's target some elements.  How about we start with the first section. 

```css
@media screen and (max-width: 768px) {
 	.main-content .section1 {
		grid-column: 1 / 2;
		grid-row: 1 / span 2;
	}
}
```



We won't see anything until set the viewport for tablet.

<img src="https://i.imgur.com/q582ihr.png">

Once that has been done we should see `section #1` is now taking up less space. 

<img src="https://i.imgur.com/u3sTjHR.png" width=400/>

**Section #2**

Now let's add the css for `section #2`.

```css
@media screen and (max-width: 768px) {
 	.main-content .section1 {
		grid-column: 1 / 2;
		grid-row: 1 / span 2;
  }
  .main-content .section2 {
		grid-column: 2 / 4;
		grid-row: 1 / 3;
	}
}
```


Here is the design.

<img src="https://i.imgur.com/JPqMGhi.png" width=400/>

**Questions:** Has the element moved? What has changed?

<hr>

#### <g-emoji class="g-emoji" alias="alarm_clock" fallback-src="https://github.githubassets.com/images/icons/emoji/unicode/23f0.png">⏰</g-emoji> Activity - 1min

- Try deleting **section #3** in DevTools and see what happens. 

When asked slack your response in a thread created by the instructor

<hr>

#### Complete the Tablet Design

Here is the remaining CSS needed to implement the Tablet design. 

```css
@media screen and (max-width: 768px) {
	.main-content .section1 {
		grid-column: 1 / 2;
		grid-row: 1 / span 2;
	}

	.main-content .section2 {
		grid-column: 2 / 4;
		grid-row: 1 / 3;
	}

	.main-content .section3 {
		grid-column: 1 / 2;
		grid-row: 3 / 4;
	}

	.main-content .sidebar1 {
		grid-column: 2 / 4;
		grid-row: 3 / 4;
	}

	.main-content .sidebar2 {
		display: none;
	}
}
```



#### Complete the Mobile Design

Before we implement the final design let's first talk about the `hamburger` menu.  This is font provided by font-awesome. 

```html
<i class="fas fa-bars fa-2x"></i>
```

<hr>

:question: What css property is being targeted to hide the icon when it's not needed and what is the value?

:question: What value is being used to make the icon visible again? 

<hr>

#### <g-emoji class="g-emoji" alias="alarm_clock" fallback-src="https://github.githubassets.com/images/icons/emoji/unicode/23f0.png">⏰</g-emoji> Activity - 10min

<!-- - Take a moment to examine the `mobile version` of the site [deployed version](http://seir-responsive-design.surge.sh/) site -->
- Take a moment to examine the **mobile version** of the site 
- Examine which elements have moved or are no longer there
- Write a **media query** that targets a max-width of 425px
- Add the **css** needed to target those elements and implement the design

Mobile Layout: 

<img src="https://i.imgur.com/Ei5DoYi.png">

## Thinking responsively

When planning your site, don't think about a piece of paper on a desk with stuff
drawn on it. That's a fixed layout! Instead, think in components and think about
how those components will look on different devices.

Start from the mobile layout and scale up when designing your page. Most CSS
frameworks are mobile-first, mobile is a huge portion of web traffic, and it's
easier to scale up and add items than cram stuff into a small space.

It's 2020. We don't build non-responsive websites anymore!

<hr>

## Bonus

Download and Install [https://responsively.app/](https://responsively.app/)

This will allow you to develop a site and visualize all viewports simultaneously 

<img src="https://i.imgur.com/N09b1cm.png" width=500/>





## Resources

- [Responsive Web Design](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/#media-queries)
- [A list of device viewport sizes](http://viewportsizes.com/)
- [Breakpoints](https://medium.freecodecamp.org/the-100-correct-way-to-do-css-breakpoints-88d6a5ba1862)
