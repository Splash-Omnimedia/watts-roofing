# Watts & Associates Roofing: Blog Mockups

HTML/CSS mockups for two new pages on [wattsroofing.com](https://www.wattsroofing.com/):

- **News & Updates** (`blog-overview.html`): blog archive with a 4-column card grid, search, and load-on-scroll.
- **Blog post** (`blog-post.html`): single article with the featured image beside the title, date, share links, article body, and a back button.

The header, footer, colors, fonts, and buttons were rebuilt from the live site's stylesheets (Divi 5 Theme Builder and the `dctroofing` child theme), so the pages match the current site.

## Viewing

- **Locally:** open `index.html` (or either page) in a browser. No build step.
- **GitHub Pages:** in the repo, go to Settings → Pages, choose "Deploy from a branch," select `main` and `/ (root)`. `index.html` redirects to the News & Updates page.
- **Single-file versions:** `mockups/` has both pages with CSS and images embedded, for emailing or sharing without the rest of the folder.

In this demo, every card links to the one sample post.

## Structure

```
index.html            Redirects to the News & Updates page
blog-overview.html    News & Updates (archive) page
blog-post.html        Single blog post page
css/watts-blog.css    All styles, shared by both pages
images/
  photo-*.jpg         Project photos, 1000×700 (post hero and in-article images)
  thumb-*.jpg         Same photos at 640×448 (card thumbnails)
  logo-50th.png       Logo (from the live site)
  badge-*.png/.webp   Footer association badges (from the live site)
mockups/              Self-contained single-file versions of both pages
```

## Design tokens

| Token | Value | Use |
|---|---|---|
| `--wr-red` | `#f02d3a` | Buttons, date tags, accents, footer background |
| `--wr-navy` | `#082c4b` | Menu, card titles, headings |
| `--wr-navy-btn` | `#1d3d7c` | Estimate Request button |
| `--wr-sky` | `#cde6f5` | Button hover |
| `--wr-peach` | `#ffe0b5` | Top bar |
| `--wr-near-black` | `#0a0002` | Footer call-to-action box |
| `--wr-radius` | `10px` | Cards, title tab, footer CTA |
| Font | Merriweather (Google Fonts) | All text |

Responsive breakpoints follow Divi: 980px (tablet) and 767px (phone). The grid goes 4 → 3 → 2 → 1 columns.

## Notes for WordPress / Divi implementation

- **Header and footer** are hand-built copies for the mockup only. In production, keep the existing Divi Theme Builder header and footer and build just the page body.
- **Load on scroll:** `blog-overview.html` renders the first 8 posts in HTML. Later posts come from mock JSON (`#wr-more-posts`) through `fetchNextBatch()`. Replace that function with a request to the WordPress posts API, for example `/wp-json/wp/v2/posts?per_page=4&page=N&_embed`. Without JavaScript, the page shows a link to older articles instead.
- **Search** filters by post title in the browser. The form already submits to `/news/?s=term`, so it can use WordPress's built-in search (which also searches article text), or the posts API's `search` parameter.
- **Share links** are built in JavaScript from the page URL. On WordPress, output them server-side with `get_permalink()` and `get_the_title()`. Included: Facebook, X, LinkedIn, Pinterest, email, text message, copy link, and print.
- **Footer badges:** the Columbia Chamber widget and the live BBB seal are third-party scripts on the live site. They're left out here, and a static BBB image stands in.
- **Mobile menu** shows top-level links only. The live site's Divi mobile menu handles submenus.
- **Accessibility:** keyboard focus styles, screen-reader announcements for search results and newly loaded posts, and reduced-motion support are included.

## Content

Post titles, dates, and article text (lorem ipsum) are placeholders. Photos are Watts & Associates project photos.
