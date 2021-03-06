# Shrewd Learning - Shrewdies.com source

Most visitors should start with Issues or Discussions.

Because thes notes are intended for developers who want to collaborate with coding rather than with content.

1. Trial Deployment after committing 1st Config Changes (minimal changes to make sure deployment works).
2. Import WP or Add Admin (gets content). Note, for WP Transmigration, there are steps needed to prepare the zip file for import. E.g., remove Cloudflare apps, check footer, create Simply Static file.
3. Complete config changes. Aim is for all these to be in `site/globals/site.json`. But otherwise search for `UpdateThis`.
4. Create pre-launch content.

## 1. 1st Config Files
- This readme project note
- site/globals/site.json

## 2. Optional Import WP
- Download zip to wp folder
- extract zip
- rename wp/index.html 
- delete zip

If you're not importing WordPress, you can optionally remove the config instruction:
- eleventy.config.js config.addPassthroughCopy({ "wp/": "/" })

## 3. Look and Feel
These are current working notes. Eventually, this is about setting colors, background-image (if any), header images.

- resources/scss/04-layout/_site.scss: change background to image to a different color. Not sure if this needs changing in main.css and/or main.min.css *
- ✅ site/includes/components/nav.njk: Change link to WP version of About Page or to appropriate blog post. But this shouldn't be necessary - see frontmatter of index.md because relevant blog (or other page) should be capable of linking without editing nav.njk
- ✅ site/index.md: rewrite.
- site/includes/components/footer.njk: Change footer links. But these need updating as new admin pages are created. Should also include a feedback link direct to issues.
- site/includes/components/footer.njk: Change disclaimer
- ✅ Change favicon.icon (root) & images/meta/apple-touch-icon.png. 
- review this README. Usually including screenshot and important user links before any technical notes.

* I got confused by the way css works in this setup and I hacked the background image 
in css/main.css and css/main.min.css which seem identical. Need to learn the 'right' way to edit css in this template! Which is probly something to do with this note in the original readme...

### The build pipeline

[Laravel Mix](https://laravel-mix.com/docs/5.0/basic-example) gives us a nice API layer on top of Webpack. Skeleventy uses a simplistic set up, but you _can_ take advantage of extending Mix with custom Webpack configurations, code splitting and plugins such as PostCSS, if you so wish.

You'll find the site's uncompiled SCSS and JS within `resources/` where Mix will be watching these directories for any changes. **Tip:** _it's best to always restart the server when creating any new partials or folders_

#### SCSS

- `scss/` is structured into opinionated sub folders
- The `_config.scss` file is where you can change the site's colours and the utility classes generated by Gorko

## 4. Start Blog

Amend or replace examples. Note, this will eventually include all admin pages as blog posts with 'using' tag.

## 5. Other Notes

- Added non-nav collection pages to menu: site/includes/components/mobile-nav.njk and site/includes/components/nav.njk
- Added Pagination:
  - site/includes/components/pagination.njk (Needs styling to professional standards)
  - site/includes/layouts/blog.njk (code added at end of card grid)