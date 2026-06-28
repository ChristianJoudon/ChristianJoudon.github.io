# christianjoudon.github.io — new site

A single, self-contained personal site. Everything (styles, scripts, and the five
project screenshots) is built into `index.html`. The only external thing it loads
is the web fonts from Google Fonts. There is no build step.

## What is in this folder

- `index.html` — the entire website, one file.
- `Christian_Joudon_Resume.pdf` — linked by the "Résumé" buttons in the site.
- `.nojekyll` — tells GitHub Pages to serve the files exactly as they are.

## How to deploy (GitHub Pages)

Your repository is `ChristianJoudon/ChristianJoudon.github.io`, which already
contains a `.nojekyll` file, so GitHub serves static files directly.

1. Replace the old `index.html` at the root of the repo with the `index.html` in this folder.
2. Upload `Christian_Joudon_Resume.pdf` to the root of the repo (so the Résumé links resolve).
3. Keep your existing `favicon.ico` if you want the browser tab icon.
4. Commit and push. The live site at https://christianjoudon.github.io updates within a minute.

That is all that is required.

## Optional cleanup

The old site was built on the TechFolio Jekyll theme. The new site does not use any
of it. Once you are happy with the new page, you can delete these leftover files and
folders from the repo to keep it tidy (none of them are referenced anymore):

`_config.yml`, `_data/`, `_includes/`, `_layouts/`, `css/`, `essays/`, `projects/`,
`Gemfile`, `Welcome_To_Colab.ipynb`, and the loose stock images at the repo root.

Leave `index.html`, `Christian_Joudon_Resume.pdf`, `.nojekyll`, and `favicon.ico`.

## Editing later

Open `index.html` in any editor. The content is plain HTML in readable sections
(About, Experience, Selected Work, Toolkit, Education, Writing, Contact). To swap a
project screenshot you would replace the corresponding `data:image/jpeg;base64,...`
string, but for small text edits you can just type directly into the markup.
