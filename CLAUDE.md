# CLAUDE.md

Personal website of Julien Bastin, served at [julienbastin.be](https://julienbastin.be). The site is a single static CV page: plain HTML and CSS, with no build step, no framework and no package manager.

## Structure

```
www/                 deployed folder (the web root on the host)
  index.html         the whole CV page
  style.css          the only stylesheet
  .htaccess          Apache config for the host
  img/               photos, background, favicon, project images
  pdf/               master's thesis (Sensor_fusion.pdf)
  README.md          credits for the original "Oh, So Simple HTML CV" template (flynerd)
README.md            repository overview
```

## Page content

- **Language**: all page content is in **English**. Source material (for example the Centran CV in .docx) is often in French: translate it, and keep the tone and wording consistent with the rest of the page.
- **Section order**: Experience (always open), then Skills, Education, Projects, Courses & Workshops.
- **Collapsible sections**: every section except Experience is a `<details class="collapsible" id="...">` with an `<h3>` inside its `<summary>`. The inline script at the bottom of `index.html` opens the matching `<details>` when a `#anchor` link is clicked or the page is loaded with a hash. New sections should follow the same pattern and be added to the `ul.nav` menu.
- **Experience**: one `<article>` per employer/client engagement, most recent first. Each has a `.job-title` block (period, company, position, client), a "Tech stack" line (items separated by ` / `) and a `ul.job-description` list. Projects are `<li>` entries: `<strong>Project name</strong> <span class="period">(MM.YYYY - Now)</span>: description.`
- **Dates**: `MM.YYYY` format, `Now` for ongoing work.
- **Skills**: the Frameworks & Tools list is a `<dl class="tools">` with one line per category. Keep it short: add a tool to an existing category rather than creating a new one.
- External links open in a new tab (`target="_blank"`).

## Styling

- Font: Raleway (Google Fonts). Icons: Font Awesome kit loaded in `<head>`.
- Accent colors: `#509e98` / `#1C9C94` (teal), greys `#889499` and `#A7B8BF`.
- Responsive breakpoints: 768px and 576px (see the media queries at the end of `style.css`).

## Deployment

- Hosted on **Hostinger**. Deploy by uploading the content of `www/` over FTP with **FileZilla** (overwrite existing files).
- **CSS cache busting**: `index.html` loads `style.css?v=N`. Whenever `style.css` changes, **increment `N`** in `index.html` and upload both files. Otherwise browsers keep the old stylesheet even after the Hostinger cache is cleared.
- To check a deployment, open `https://julienbastin.be/style.css` and verify it contains the latest changes, then reload the page with Ctrl+F5.

## Checking changes locally

Open `www/index.html` directly in a browser: there is nothing to build or run. Check the desktop layout and a narrow (mobile) width before deploying.

## Git

The user commits and pushes themselves: do not commit or push unless asked.
