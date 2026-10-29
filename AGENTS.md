# Homepage rules

This repo is a static single-page homepage: `index.html`, `style.css`, and `images/`. There is no build step and no framework. Keep it that way unless the owner asks otherwise.

## Source of truth for the owner's profile

The owner is Tinapat Game Limsila (GitHub: GameTL).

Before writing or changing profile content (name, title, bio, location, roles, education, awards, projects), check these sources for the current information:

- GitHub: https://github.com/GameTL. Use `gh api users/GameTL` for the profile and `gh api 'users/GameTL/repos?sort=pushed'` for recent repos.
- LinkedIn: https://th.linkedin.com/in/gametl.

Rules for conflicts and recency:

- For each fact, use the source with the most recent dated information.
- If this site already has dated content that is newer than GitHub or LinkedIn, keep the site's version and say so.
- If a source can't be read, say so. LinkedIn returns HTTP 999 to automated fetches. Do not try to get around that block. Ask the owner to paste the section or send a profile export.
- Don't invent facts. If nothing confirms a field, leave its placeholder in place.

## Content and design

- Change text and data, not the design. Keep the existing layout, class names, sections, dark mode, and the news and publication filters in `style.css` and `index.html` unless asked.
- Don't add contact details (email, phone, social handles) that the owner hasn't approved for the page. The GitHub profile contains an email. That doesn't make it approved for the site.
- Keep the HTML valid. After edits, check that every tag is closed.
- Put local images in `images/` and reference them with relative paths.
- When you update the homepage, update the profile README (`GameTL/GameTL`, README.md) in the same change, so both show the same publications, experience, education, awards, and links.
- Local dev first: keep changes uncommitted and don't push until the owner says to push.

## Search visibility (SEO)

Site-wide:

- Use one name everywhere: "Tinapat Game Limsila" (alternate name: "Game Limsila"). Don't mix other spellings into titles, citations, or alt text.
- Give each page a unique `<title>` of 60 characters or fewer, in the form "Page topic | Tinapat Game Limsila".
- Give each page a `<meta name="description">` of 120 to 160 characters that says what the page is about in plain words. Don't stuff keywords.
- Set `<html lang>` to the page's language.
- Use one `<h1>` per page, and nest headings in order (h2 under h1, h3 under h2).
- Give every image alt text that describes what it shows. Don't use generic alt text such as "Paper thumbnail" or "Profile Photo" on new content.
- Add `<link rel="canonical">` once the owner gives the final domain. Ask for it before adding the tag.
- Keep `robots.txt` and `sitemap.xml` at the site root. The sitemap lists every page that should be indexed, and `robots.txt` points to it. Update the sitemap whenever a page is added or removed.
- Don't add `noindex` unless the owner asks.
- Don't add "best viewed on desktop" notices. Every page must work on phones.

Homepage:

- Keep the Person JSON-LD in `<head>` in sync with the profile: name, alternate name, jobTitle, and `sameAs` links to GitHub and LinkedIn. Add Google Scholar once the owner gives the URL.

Publications:

- Use the exact title from the DOI record (Crossref) so search engines and Google Scholar match the paper.
- For each publication page, add Google Scholar citation meta tags: `citation_title`, one `citation_author` per author, `citation_publication_date` (YYYY/MM/DD), `citation_journal_title` or `citation_conference_title`, and `citation_doi`. Add `citation_pdf_url` only when the PDF is public.
- Add a ScholarlyArticle JSON-LD block with headline, author, datePublished, isPartOf (the venue), and identifier (the DOI).
- In the publication list, link each entry to its DOI or to its own page. Don't link to `#`.

Blog posts (when the blog is added):

- Give each post its own URL: lowercase, hyphenated, and descriptive, such as `/blog/waste-sorting-bin/`. Don't change a slug after publishing. If you must, add a redirect from the old URL.
- Give each post a unique title, a description, a visible date, and BlogPosting JSON-LD with headline, description, author, datePublished, and dateModified.
- Link each post from the blog index and from the homepage, and link related posts to each other.
- Structure each post with headings and use descriptive link text, not "click here".

## Sync

When the owner asks to sync, check these four sources and update the site to match. Use the most recent dated information for each item.

- Google Scholar: https://scholar.google.com/citations?user=Z4n4YowAAAAJ&hl=en. Check every page of the works list, because the list is paginated with "Show more".
- alphaXiv: https://www.alphaxiv.org/@tinapat-game-limsila.
- LinkedIn: https://th.linkedin.com/in/gametl. If it returns HTTP 999, don't work around it. Ask the owner to paste the section or send a profile export.
- GitHub: https://github.com/GameTL, using `gh api`.

Before adding a publication, verify its title, authors, venue, and year against Crossref (by DOI or title) or arXiv. Use the exact title from that record. Add a DOI or arXiv link to every new entry, and make a venue-card thumbnail for it in the same style as the others.

## Git and preview

- Don't commit or push unless the owner asks.
- To preview locally, run `python3 -m http.server 8000` from the repo root and open http://127.0.0.1:8000/.
