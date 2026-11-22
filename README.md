# s1mpnyS.github.io

Personal academic website of **Gia Phong Ngo**, built from the [al-folio](https://github.com/alshedivat/al-folio) Jekyll template.

## Publish on GitHub Pages (first time)

1. Create a **public** repository named exactly `s1mpnyS.github.io`. For the commands below, start with an empty repository.
2. Extract the site source. From the folder that contains `_config.yml` and `.github/`, push the source files to `main`.

   ```bash
   git init -b main
   git add -A
   git commit -m "Add academic website"
   git remote add origin https://github.com/s1mpnyS/s1mpnyS.github.io.git
   git push -u origin main
   ```

   For an existing repository, copy the source files into its checkout and commit and push them on `main`.

3. Open **Settings → Pages** and choose **GitHub Actions** under **Build and deployment → Source**.
4. Open **Actions → Deploy site → Run workflow**, select `main`, and run it. After the `build` and `deploy` jobs finish, open the deployment URL in the run or visit <https://s1mpnys.github.io/>. Subsequent pushes to `main` build and deploy the site automatically.

## Where things live

| What                       | File                                                             |
| -------------------------- | ---------------------------------------------------------------- |
| Photo                      | `assets/img/prof_pic.jpg` (replace the "GP" placeholder, square) |
| Bio on the home page       | `_pages/about.md`                                                |
| Name, site settings        | `_config.yml`                                                    |
| Email / GitHub / LinkedIn  | `_data/socials.yml`                                              |
| Publications               | `_bibliography/papers.bib` (`selected = {true}` shows on home)   |
| Publication thumbnails     | `assets/img/publication_preview/`                                |
| Venue badges and colours   | `_data/venues.yml`                                               |
| CV page + downloadable PDF | `_data/cv.yml` (PDF is rendered with RenderCV on every deploy)   |
| Projects                   | `_projects/*.md`, images in `assets/img/projects/`               |
| Teaching                   | `_pages/teaching.md`                                             |
| News on the home page      | `_news/*.md`                                                     |

## Common edits

- **A paper gets accepted:** in `papers.bib`, remove `note = {Under review}` and add `doi = {...}`, `html = {https://...}` or
  `pdf = {https://...}`; buttons appear automatically. Do the same in `_data/cv.yml`.
- **Add a blog later:** put posts in `_posts/` and set `nav: true` in `_pages/blog.md`.
- **Google Scholar / ORCID:** uncomment the lines in `_data/socials.yml`.

Grades are intentionally not shown anywhere on the site or in the generated CV PDF.

## Preview locally (optional)

Use Ruby 3.3, Bundler 4.0.6, Node.js 24, and ImageMagick with its `convert` command available. On Windows, use RubyInstaller with Devkit and check that `convert -version` identifies ImageMagick. To enable the CV download in a local build, render the PDF with Python 3.13 before starting Jekyll.

```bash
python -m pip install 'rendercv[full]==2.8'
cd _data
rendercv render cv.yml --quiet --settings ../assets/rendercv/settings.yaml --design ../assets/rendercv/design.yaml --locale-catalog ../assets/rendercv/locale.yaml
cd ..
```

```bash
bundle install
bundle exec jekyll serve   # http://localhost:4000
```

See `docs/CUSTOMIZE.md` and `docs/INSTALL.md` for upstream theme reference. Use the publishing steps above for this site.
