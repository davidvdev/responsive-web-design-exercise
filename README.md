# Responsive Web Design

## How to think about building websites responsively

The goal of this mini-lesson is to start thinking in a new way about how websites should be structured.

We'll talk about the problems with building fixed width websites and the ways to avoid them.

On some websites, over 40% of the traffic comes from mobile devices or tablets. Many people's only connection to the internet is through their smartphone.

Addressing this problem is not just a matter of aesthetics, but functionality and even more so, accessibility. Catering to everyone who visits your site is absolutely in your best interest.

### The problem

Websites are often built with a desktop environment in mind. Think about a long sheet of paper in portrait mode - it's got a specific width, and you scroll up and down the page.

The part of the site that you can see at any given time is what's inside the `viewport`. It's just like it sounds. You can think of the viewport as the window to the site - the whole site is there, but you can only look at a little bit at a time.

![viewport](./images/viewport.png)

Building websites for a desktop environment means, generally, you're operating with a minimum width of 900 pixels. It also means the content inside that 900px is either:

* A percentage of the width (e.g. 50%)
* A fixed width (e.g. 450px)

Here's a basic example of a site with a sidebar:

![normalwidth](./images/normal.png)

Let's think about what might happen when we look at this page on a smaller screen, like a phone or tablet. Or for something comparable, imagine what it would happen if you took your web browser and dragged/resized it to make it skinnier.

![squished](./images/squished.png)

#### Best case scenario

The phone will render the page with all of its features at normal proportions, just super zoomed out. If you've ever used a website like this you understand the frustrations - horizontal scrolling, tiny text, everything looks like it's made for ants.

![websiteforants](./images/what-is-this-a-website-for-ants.jpg)

Here's a screenshot of github's site viewed on my phone. ANTS!

![github-desktop](./images/github-screenshot.png)

#### Worst Case Scenario

The worst case scenario is like the squished image above. All of the content formatting is basically unreadable because it's still 1/3 of the screen, but the screen is way smaller now.

### Live example

Try out the codepen example. Resize your browser width and see what happens to the content.

https://codepen.io/jabyess/pen/mLpxym

### Bad solutions

In the olden days, some websites had two versions: desktop and mobile.

You may even still see sites that do this. Visiting `https://www.reddit.com` from your desktop works great, but visit it from your phone and you'll probably be redirected to `https://m.reddit.com` (if they still do that).

These are totally different sites! Different html, css, and javascript being served to the same users, just because they logged in from their phone.

THIS IS TERRIBLE! Now you (the developer) have to maintain two completely different websites. They're probably both going to suffer as a result.

### Introducing Media Queries

Media queries are a CSS feature that lets you define properties and values at different browser widths.

Here's what a media query looks like:

```css
@media screen (max-width: 500px) {
  width: 100%;
}
```

Let's break it down:

* `@media` is the start of the declaration. required.
* `screen` tells the browser to only use this on the screen. Another option is `print` for pdfs or printing out html pages. optional.
* `(max-width: 500px)` is one of the parameters you can specify. There are lots. This tells the screen to only apply this query when the screen width is BELOW 500px. required.

> For reference: https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries

### Breakpoints

Breakpoints are just a set (usually 3-5) of viewport widths, that you use in conjunction with media queries.

You want your website to react predictably - therefore you should decide when you want your media queries to do their magic, and stick to that same set.

Here's what [bootstrap](https://getbootstrap.com/docs/4.1/layout/overview/), the most popular CSS framework uses:
```css
/* Small devices (landscape phones, 576px and up) */
@media (min-width: 576px) { ... }

/* Medium devices (tablets, 768px and up) */
@media (min-width: 768px) { ... }

/* Large devices (desktops, 992px and up) */
@media (min-width: 992px) { ... }

/* Extra large devices (large desktops, 1200px and up) */
@media (min-width: 1200px) { ... }
```

You're not tied to using only these specific widths, but for now let's keep them because they're there.

### Let's use all this stuff now

We'll use these media queries and breakpoints together to make sure that our website looks nice on all sized devices!