# 11ty Blog Starter

Based of https://github.com/11ty/eleventy-base-blog

## Setup

After you clone the repo

```
npm i
npm run serve
```

This starts 11ty on port 8080 and runs in watch mode, so any change you make to the `src` folder triggers a browser reload.

## Structure

The code goes into `src` and the static build is created in `dist`. Assets (icons, images) go to `img` and get copied into `dist` at build time. Content is written in `src/posts`. Each post will generate a new page in the output.

## Features

### Full markdown support

All your content can be in markdown and gets converted into html via [markdown-it](https://github.com/markdown-it/markdown-it). For each md file, there are a couple of fields you can configure in the frontmatter, like the cover image for an article, the slug and the tags.

Other files are generated based on nunjucks (.njk). There's an index page and separate pages for the list of articles, list of categories (tags) and articles for a certain tag. There's also a 404 page.

### Layout files

You have two layout pages, one is the `base.njk` layout that has the `<head>` tags and the main structure in the body. Then each blog post uses the `post.njk` for the content outside the actual markdown generated code.

### Starter theme

The css goes into `src/_includes/css`. You can define different files if your project scales and include them all in the `postcss` shortcode (check the `.eleventy.js` config file). All the css goes through postcss as `autoprefixer` is applied. The resulting style is minified and injected in the `<head>`.

The theme is based on a set of css custom properties for things like color, typography and spacing. There are also a set of elements which are styled: links, link buttons, post cards and so on.

### Lazy Images

The project uses the 11ty plugin for lazy images to defer loading the images until they are actually needed. This is very useful if you write long blog posts with a lot of images as a placeholder is added instead of the real image until you scroll the image into view. Lazy images creates a `.lazyimages.json` with all the data about the images in the projects and uses that file for subsequent builds for speed.

### SEO Focus

There are a couple of features you get out of the box that help you with SEO and social media cards.

- `sitemap.xml.njk` generates the sitemap based on your links
- `robots.txt` is copied over to the dist folder
- title, description and social media headers are generated based on data from `src/_data/metadata.json`.

### Others

There are a couple of other plugins offering different functionality

- svg-contents: inlines svg files
- table of contents: generates toc from markdown content
- reading time: computes reading time from markdown content
- markdown-it-link-attributes: adds target "\_blank" and rel "noreferrer noopener" for absolute links in markdown
