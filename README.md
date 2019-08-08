# Responsive Web Design

## How to think about building websites responsively

The goal of this mini-lesson is to start thinking in a new way about how
websites should be structured.

We'll talk about the problems with building fixed width websites and the ways to
avoid them.

On some websites, over 40% of the traffic comes from mobile devices or tablets.
Many people's only connection to the internet is through their smartphone.

Addressing this problem is not just a matter of aesthetics, but functionality
and even more so, accessibility. Catering to everyone who visits your site is
absolutely in your best interest.

## The problem

Websites are often built with a desktop environment in mind. Think about a long
sheet of paper in portrait mode - it's got a specific width, and you scroll up
and down the page.

The part of the site that you can see at any given time is what's inside the
`viewport`. It's just like it sounds. You can think of the viewport as the
window to the site - the whole site is there, but you can only look at a little
bit at a time.

![viewport](./images/viewport.png)

Building websites for a desktop environment means, generally, you're operating
with a minimum width of 900 pixels. It also means the content inside that 900px
is either:

- A percentage of the width (e.g. 50%)
- A fixed width (e.g. 450px)

Here's a basic example of a site with a sidebar:

![normalwidth](./images/normal.png)

Let's think about what might happen when we look at this page on a smaller
screen, like a phone or tablet. Or for something comparable, imagine what it
would happen if you took your web browser and dragged/resized it to make it
skinnier.

![squished](./images/squished.png)

### Best case scenario

The phone will render the page with all of its features at normal proportions,
just super zoomed out. If you've ever used a website like this you understand
the frustrations - horizontal scrolling, tiny text, everything looks like it's
made for ants.

![websiteforants](./images/what-is-this-a-website-for-ants.jpg)

Here's a screenshot of github's site viewed on my phone. ANTS!

![github-desktop](./images/github-screenshot.png)

### Worst Case Scenario

The worst case scenario is like the squished image above. All of the content
formatting is basically unreadable because it's still 1/3 of the screen, but the
screen is way smaller now.

## Live example

Fork and clone the
[starter code for this lesson](https://git.generalassemb.ly/dc-wdi-fundamentals/responsive-web-design-starter-code)

Open up the directory in Sublime Text and open the HTML in your browser with the
CLI command `open index.html`

Resize your browser width and see what happens to the content.

## Bad solutions

In the olden days, some websites had two versions: desktop and mobile.

You may even still see sites that do this. Visiting `https://www.reddit.com`
from your desktop works great, but visit it from your phone and you'll probably
be redirected to `https://m.reddit.com` (if they still do that).

These are totally different sites! Different html, css, and javascript being
served to the same users, just because they logged in from their phone.

THIS IS TERRIBLE! Now you (the developer) have to maintain two completely
different websites. Both versions, and you, are all probably both going to
suffer as a result.

## Introducing Media Queries

Media queries are a CSS feature that lets you define properties and values at
different browser widths.

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
  500px. required.

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

## Let's use all this stuff now

We'll use these media queries and breakpoints together to make sure that our
website looks nice on all sized devices!

Let's make some changes to the starter code to make our site responsive.

The first thing we should do is get a sense of all the different components that
we want to affect using media queries.

In this case, we'll start with the `.text` and `.sidebar` classes, because as we
saw before, they have fixed widths and are full of content that gets squished on
small screen sizes.

Since we've decided on our breakpoints above, let's write a media query and
create a new class. We'll put this new class on whatever elements we want to
change with the media query.

We could also just modify the classes we already have by wrapping them in media
queries, but that's less flexible, and way more repetitive.

> Note: we're using max-width here instead of the min-width examples that
> bootstrap has.

```css
@media screen and (max-width: 576px) {
  .small-100 {
    width: 100%;
  }
}
```

Now go ahead and add that class to the appropriate elements. Resize the window.
WHAT IS HAPPENING??!

The sidebar should pop down below the text content when the viewport width gets
smaller than 572px.

Feel free to add more media queries at different widths and use them to create
different classes!

## What else can we do with media queries?

Obviously, width isn't the only property we can change using a media query. We
can change **any** css property.

Add a new class to the small media query called `hidden-small`

```css
@media screen and (max-width: 576px) {
  .small-100 {
    width: 100%;
  }
  .hidden-small {
    display: none;
  }
}
```

Now go apply that class to a couple of the `.navbar-item` elements, and watch
them disappear when you shrink your browser window.

**AMAZING!!!**

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

## Bonus Aside: the Grid

Working with random percentages is great and all, but having consistency will
take you much further and keep you from pulling your hair out.

Enter: the GRID

![THE GRID](./images/tron_grid.jpg)

Instead of picking 40, 50, 60, whatever percent, many frameworks use 12 columns.

The basic idea is that columns are equal to n divided by 12. So an element that
is 3 columns wide === 3/12, which equals 25% width.

5 columns === 5 / 12, or 41.6666667% width.

Don't worry about the weird numbers, the browser does the math for us.

Bootstrap uses this to generate CSS classes for each breakpoint and column
combo. Example css classes:

- `col-xs-12` means 12 columns wide at xtra small width
- `col-md-4` means 4 columns wide at medium width
- `col-lg-2` means 2 columns wide at large width

We can apply these classes to any elements that we want. Generally, we apply
them to elements that we want to act as containers. Then those elements resize
depending on the screen size.

## Resources

- A list of device viewport sizes: http://viewportsizes.com/
- [Solution branch for the starter code](https://git.generalassemb.ly/dc-wdi-fundamentals/responsive-web-design-starter-code/tree/solution-responsive)
  - can also run `git checkout solution-responsive` in the repo we forked and
    clone earlier.
