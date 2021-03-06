---
title: How to Switch Logo in Dark Mode
date: 2020-07-03T10:52:03.096Z
published: false
tags:
  - CSS
canonical_url: true
description: I share how I was able to switch the color of my logo in dark mode
  using CSS custom properties.
---
I designed my website with two versions of the logo - one for light mode and another for dark mode. In this article, I'll share how I switched the color of the logo in light/dark mode.

![Light and Dark Logo Grid](/images/uploads/untitled-design.png)

When it came to implementing this design, I was a bit confused about how to go about switching between these two versions when either dark/light mode is selected.

I found a way to do this, and I'll share how I was able to achieve it. I'm open to hearing how you'll typically implement this if you were trying to. [You can reach out on Twitter](https://twitter.com/lauragift_) always open to learning new methods of solving a problem.

Let's dive into it!! So I've got an image tag with the dark-outline logo. It'll serve as the default logo that you see when you're on light mode.

```html
<img class="logo" src="../assets/img/logo.png" alt="original logo" />
```

## Solution: Using CSS Variables

We can use CSS custom properties(CSS Variables) to solve this problem. Here's what I did, I defined a variable in the `variables.scss` called logo for both dark and light mode and set it as the background image, which you'll see in a moment.

```css
body {
  --logo: url(logo.png) no-repeat;

}

body[data-theme="dark"] {
  --logo: url(logo-light.png) no-repeat;
}
```

Then I applied the following style to the `.logo` class on the image. It sets the background image to both versions of the logo depending on which one is selected. The background-size and height properties help position the image directly on top of the original image.

```css
.logo {
  display: block;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  background: var(--logo);
  background-size: 60px;
  height: 80px;
  padding-left: 100px;
}
```

![switching between dark and light mode](/images/uploads/4vw3ldyk9v.gif)

That's it! I now have two different versions of my logo for dark and light mode. If you're interested in seeing the implementation in more detail, the code for my website is open-source, and [you can check it out](https://github.com/lauragift21/giftegwuenu.dev/blob/master/src/components/Nav.vue).