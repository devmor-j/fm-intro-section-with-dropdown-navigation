# Frontend Mentor - Intro section with dropdown navigation solution

This is my solution to the [Intro section with dropdown navigation challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/intro-section-with-dropdown-navigation-ryaPetHE5). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Useful resources](#useful-resources)
- [Author](#author)

## Overview

### The challenge

Users should be able to:

- View the relevant dropdown menus on desktop and mobile when interacting with the navigation links
- View the optimal layout for the content depending on their device's screen size
- See hover states for all interactive elements on the page

### Screenshot

Desktop 1536px

![Desktop](./screenshot/Desktop%20%5B1536px%5D%20-%20Intro%20section%20with%20dropdown%20navigation.webp)

Mobile 375px iPhone 5/SE

![Mobile](./screenshot/Mobile%20%5B375px%20open%20drawer%5D%20-%20Intro%20section%20with%20dropdown%20navigation.webp)

### Links

- Solution URL: [Github repository](https://github.com/devmor-j/fm-intro-section-with-dropdown-navigation)
- Live Site URL: [Hosted on Github Pages](https://devmor-j.github.io/fm-intro-section-with-dropdown-navigation/)

## My process

### Built with

- Semantic HTML5 markup
- Mobile-first workflow
- [Bootstrap (v5.x)](https://getbootstrap.com/) - Build fast, responsive sites with Bootstrap
- [SASS](https://sass-lang.com) - CSS with superpowers
- [Vite.js](https://vitejs.dev/) - Next Generation Frontend Tooling
- [Minified html](https://github.com/vbenjs/vite-plugin-html) and [compressed png](https://github.com/vbenjs/vite-plugin-imagemin) pipeline

**Note: These are just examples. Delete this note and replace the list above with your own choices**

### What I learned

Using Bootstrap is hard! I would probably swtich back to my Tailwind setup for css styling.

Even changing color is a pain :| not to mention responsive classes and hover states :)

One hack that I have to do was changing default arror icons on dropdown menu. assume you have something like this:

```html
<li class="nav-item dropdown">
  <a class="nav-link dropdown-toggle" href="#" id="navbarDropdownMenuLink" role="button" data-bs-toggle="dropdown" aria-expanded="false">
    Features <!-- dropdown header -->
  </a>
  <ul class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
    <li>
      <a class="dropdown-item" href="#">Todo List</a>
    </li>
    ...
    <!-- list continues -->
    ...
    <li>
      <a class="dropdown-item" href="#">Planning</a>
    </li>
  </ul>
</li>
```

In order to use your own arrow shape for dropdown menus, we have to override some bootstrap classes that will reset bootstrap default icons. after that make sure layout still looks good and then bring in your own:

```scss
// first you have to hide default arrows by overriding this calss
.dropdown-toggle::after {
  color: transparent;
  display: none;
}

// now style micro layout change
// depends on your styles
// but make sure you don't break something
.dropdown-toggle {
  display: flex;
  flex-direction: row-reverse;
  justify-content: start;
  gap: 0.75rem;
}

// add your own icon for 'closed state' (down arrow)
.dropdown-toggle::before {
  margin-top: -0.125rem;
  content: url("/images/icon-arrow-down.svg");
  // please note that 'background-image' won't work here
  // instead use 'content' property
}

// everytime user clicks on dropdown menu,
// change arrow icon to 'opened state' (up arrow)
.dropdown-toggle:focus::before {
  content: url("/images/icon-arrow-up.svg");
}
```

Well I don't have to hack anything in [Tailwind](tailwindcss.com/) and classes are atomic and well-named. Also these bootstrap hacks make project very hard to maintain. Still there might be better solutions but I don't think their gonna be much better than this!

### Useful resources

Make sure to checkout [TailwindCSS](tailwindcss.com/) and give it a try!

## Author

- Frontend Mentor - [@devmor-j](https://www.frontendmentor.io/profile/devmor-j)
