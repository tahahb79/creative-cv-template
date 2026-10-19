# Creative CV Portfolio

A lightweight, configuration-driven personal portfolio and CV website built with HTML, vanilla JavaScript, Tailwind CSS, and GitHub Pages. Create a repository from this template, update the JSON configuration files, and publish a personal portfolio without changing the page templates.

**Live demo:** <https://tahahb79.github.io/creative-cv-template/>

## Quick Start

1. Click **Use this template** → **Create a new repository** at the top of this page.
   - Name it `your-username.github.io` to publish at `https://your-username.github.io/`, or use any other name to publish at `https://your-username.github.io/repository-name/`.
2. In the new repository, open **Settings → Pages** and set **Source** to **GitHub Actions**.
3. Edit the JSON files in `config/` (directly on GitHub or locally) and replace the placeholder images in `images/`.
4. Every push to `main` rebuilds and redeploys the site. If the first run failed because Pages was not enabled yet, re-run it from the **Actions** tab.

## Features

- Responsive home page with profile image and colored navigation circles
- Separate Resume and CV pages
- Projects page with local project artwork
- Publications page
- Dark mode with saved theme preference
- Google Scholar, GitHub, LinkedIn, and email links
- Relative asset and configuration paths compatible with both user sites and project sites
- Automated GitHub Pages deployment through GitHub Actions

## Pages

- `index.html`: Home page and profile introduction
- `resume.html`: Short resume view
- `cv.html`: Detailed CV view
- `projects.html`: Project portfolio
- `publications.html`: Academic publications and technical articles

## Configuration

All editable website content is stored in the `config/` directory. The JavaScript loader automatically selects the configuration file that matches the current page name.

| Page | Configuration file |
| --- | --- |
| Home | `config/index.config.json` |
| Resume | `config/resume.config.json` |
| CV | `config/cv.config.json` |
| Projects | `config/projects.config.json` |
| Publications | `config/publications.config.json` |

To customize the template:

1. Replace every `Your Name`, `your-username`, `you@example.com`, and other placeholder value in the JSON files in `config/`.
2. Replace the profile image at `images/profile-placeholder.svg`, or add your own photo (for example `images/me.jpg`) and update the `image` and `favicon` paths in the configuration files.
3. Add or replace project images in `images/` (`project-one.svg`, `project-two.svg`, `project-three.svg`) and update the corresponding paths in `config/projects.config.json`.
4. Add or remove entries in any list (jobs, projects, publications, and so on) by copying an existing entry.
5. Keep the existing JSON structure so the page loader can render each section correctly.

Optional fields:

- Social links: remove `github`, `linkedin`, `email`, or `googleScholar` from `socialLinks` to hide that icon.
- Projects: each project can have a `github` link, a `demo` link, or both.
- CV experience: leave `location` empty to hide it.

## Run Locally

A local HTTP server is required because the site loads page configuration files with `fetch`. Opening an HTML file directly with `file://` will not load the configuration correctly.

Install dependencies and build the stylesheet:

```bash
npm ci
npm run build
```

Start a local server with Python:

```bash
python3 -m http.server 8000
```

Open `http://localhost:8000` in a browser.

Available local pages:

- `http://localhost:8000/`
- `http://localhost:8000/resume.html`
- `http://localhost:8000/cv.html`
- `http://localhost:8000/projects.html`
- `http://localhost:8000/publications.html`

For live stylesheet development, use:

```bash
npm run watch
```

## GitHub Pages Deployment

The repository includes `.github/workflows/nodejs.yml`, which builds and deploys the site with GitHub Actions.

1. Push the repository to GitHub.
2. Open the repository's **Settings** page.
3. Select **Pages** under **Code and automation**.
4. Set **Source** to **GitHub Actions**.
5. Push to the `main` branch or run the workflow manually from the **Actions** tab.

The workflow installs dependencies with `npm ci`, builds `css/output.css`, creates a clean Pages artifact, and deploys it using the official GitHub Pages actions.

The site works with both deployment formats:

- User site: `https://username.github.io/`
- Project site: `https://username.github.io/repository-name/`

## Project Structure

```text
.
├── config/
│   ├── cv.config.json
│   ├── index.config.json
│   ├── projects.config.json
│   ├── publications.config.json
│   └── resume.config.json
├── css/
│   ├── main.css
│   ├── output.css
│   └── style.css
├── images/
├── js/
│   ├── config-loader.js
│   ├── init.js
│   └── theme-manager.js
├── .github/workflows/nodejs.yml
├── cv.html
├── index.html
├── projects.html
├── publications.html
├── resume.html
├── package.json
└── tailwind.config.js
```

## Customization Notes

- Use valid JSON in every file under `config/`.
- Keep paths relative rather than beginning them with `/`; this preserves compatibility with GitHub project sites.
- If a page configuration includes dynamic Tailwind classes, keep the related paths in `tailwind.config.js` content scanning.
- Keep `css/output.css` generated by `npm run build` after changing styles.
- External links should use HTTPS whenever the destination supports it.

## License

Add the license that best matches your intended use before distributing the template publicly.
