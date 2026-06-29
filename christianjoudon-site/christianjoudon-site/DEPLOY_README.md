# Portfolio site — deploy guide

Your site is now **multi-page**. The homepage is a polished overview, and every
project card and essay clicks through to its own full page. Moving the images
and styles into shared files also made `index.html` tiny, so the "too big to
paste" problem is gone.

## What's in here

Everything to upload lives in the **`site/`** folder:

```
index.html                     <- homepage (overwrites your current one)
favicon.ico
Christian_Joudon_Resume.pdf
.nojekyll
assets/
   site.css                    <- shared styling for every page
   site.js
   img/  (5 project images)
work/                          <- 10 project detail pages
   haven.html, chime.html, global-events.html, covid-nlp.html,
   uhnify.html, terran.html, audio-visualizer.html, hitech-labs.html,
   workflow-automation.html, refund-builder.html
essays/                        <- 7 essay pages
   professional-interests.html, reflecting-on-software-engineering.html,
   design-patterns.html, environmental-systems-rpgs.html,
   ai-in-education.html, ai-virtual-economies.html,
   high-dimensional-economic-modeling.html
```

These are all plain static files, so they deploy through your existing GitHub
Action with no settings to change. You only **add** files (plus overwrite
`index.html`). Nothing needs to be deleted.

## How to deploy (GitHub website)

1. Go to your repo: `github.com/ChristianJoudon/ChristianJoudon.github.io`
2. **Add file -> Upload files**.
3. Open the `site/` folder on your computer, select **everything inside it**
   (the files **and** the `assets`, `work`, `essays` folders), and drag it all
   into the upload box. The folder structure is preserved.
4. Scroll down. Make sure **"Commit directly to the `main` branch"** is selected
   (not "Create a new branch / pull request").
5. Click **Commit changes**.
6. Click the repo's **Actions** tab and wait for the build to finish with a
   green check. If it goes red, the deploy did not happen — tell me and I'll
   help read the error.
7. Open your site and **hard-refresh** (Cmd+Shift+R) to clear the cache.

That's it. Click any project card -> it opens that project's page. Essays have
their own section near the bottom, each linking to its own page.

## Preview locally first (optional)

The pages use absolute paths (`/assets/...`), which is correct for GitHub Pages
but means opening `index.html` straight off your disk won't load the styles. To
preview properly, open a terminal in the `site/` folder and run:

```
python3 -m http.server 8000
```

then visit `http://localhost:8000` in your browser.

## One thing worth adding later

Most detail pages describe the work but only a few link out: **UHnify** links to
its live site, and **Global Events** embeds its visualization. If you have live
demo URLs or public GitHub repos for any of the others (HAVEN, Chime, the HiTech
Labs site, the dashboard, the refund builder, COVID pipeline, Terran, the audio
visualizer), send them over and I'll wire them into the matching pages.
