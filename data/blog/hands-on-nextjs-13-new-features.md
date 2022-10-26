---
title: Hands on Next.Js 13 new features
date: '2022-10-26'
tags: ['NextJs', 'Vercel']
draft: false
summary: Understanding the /app directory in Next 13
images: ['/static/images/blog/next-13.png']
layout: PostLayout
canonicalUrl:
---

![](/static/images/blog/next-13.png)

# Whats on Here!

[1. Intro](#intro)

[2. Getting Started](#getting-started)

[3. Special Files](#special-files)

[4. References](#references)

## Intro

[NextJs](https://nextjs.org) has a released a new version and there are some major changes that you can read in their official [website](https://nextjs.org/13), but I'm gonna try and wrap my head around the `app` directory because layouts has been alittle pain to me in NextJs

> By default the `app` directory in Next 13 uses React Server Components(RSC), we won't be discussing about it but you can read more about it in their [docs](https://nextjs.org/docs/advanced-features/react-18/server-components)

## Getting Started

You can start by creating a new Nextjs project using `create-next-app` with the `app` directory by running 👇

```bash
    yarn create next-app --experimental-app <your-project-name>
```

or if you are using `npm` you can run the command below but I prefer using yarn

```bash
    npx create-next-app --experimental-app <your-project-name>
```

> If you are coming from a previous version or you want to set it manually I suggest having a look at the [docs](https://beta.nextjs.org) on setting the `app` directory manually

## Special files

- `layout`: this defines a layout of a web page, can be specific for a route by placing it within a folder that contains a route file or can be a root layout if placed in the `app` directory

```
|--app
    |--page.js
    |--layout.js
```

_This is the root layout and all routes inherit from this layout_

```
|--movies
    |--page.js
    |--layout.js
```

_Here the layout file is specific only for the `/movies` but also inherits the root layout route while other routes inherit from root layout if not specified_

- `page`: this file is responsible for the specific route, mapping back in previous versions of next you may refer this as `index.js` of routing in `pages` directory

```
|--app
    |--pages.js
    |--layout.js
```

_This maps to `/` of the website_

```
|--app
    ...
    |--movies
        |--page.js
    |--[animes]
        |--page.js
```

_This maps to `/movies` and `/[animes]`(a dynamic route) respectively just like in `pages` directory in the previous versions of next if you relate it with `index.js`_

- `loading`: This acts as a fallback component when a component is fetching data so it gets rendered for a short period of time until the data is fetched

  > **Note**: It can be nested also in specific routes

- `error`:😁 The name explains itself, once an error occurs this components gets rendered so you can customize it with a user friendly error message

- `not-found`: Use this to provide a Not Found Page when a not found function is thrown in a route segment

## References

[NextJs Docs](https://beta.nextjs.org)
