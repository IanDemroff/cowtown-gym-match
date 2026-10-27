# Put Cowtown Gym Match on the web (GitHub Pages)

You need a free GitHub account. Everything below happens in your web browser. No software to install.

## 1. Create the repository

1. Go to https://github.com and sign in.
2. Click the **+** at the top right, then **New repository**.
3. Repository name: `cowtown-gym-match`
4. Choose **Public**. Free GitHub Pages needs a public repository, which means anyone can see these files.
5. Leave "Add a README", ".gitignore" and "license" **unticked** (this folder already has them).
6. Click **Create repository**.

## 2. Upload the files

1. Unzip `cowtown-gym-match.zip` on your computer. You get a folder called `cowtown-gym-match`.
2. On the new repository page, click the link **uploading an existing file**.
3. Open the unzipped `cowtown-gym-match` folder, select **everything inside it** (not the folder itself), and drag it into the browser window. Folders like `vendor` and `docs` upload with their contents.
4. Check that `index.html` is in the list at the top level, not inside another folder.
5. Scroll down, type a message such as `First upload`, and click **Commit changes**.

**About hidden files:** `.gitignore` and `.nojekyll` start with a dot, so Mac and Windows may hide them and they may not get dragged in. The site works without them. If you want them: on the repository page click **Add file > Create new file**, name it `.nojekyll`, leave it empty, and commit. Do the same for `.gitignore` and paste in the text from the copy in the zip.

## 3. Turn on the website

1. In the repository, click **Settings** (top bar), then **Pages** (left menu).
2. Under **Build and deployment**, Source: **Deploy from a branch**.
3. Branch: **main**, folder: **/ (root)**. Click **Save**.
4. Wait one to two minutes and refresh. The page shows "Your site is live at" with a link like
   `https://YOUR-GITHUB-USERNAME.github.io/cowtown-gym-match/`
5. Open it, take the quiz, and try "Use my location" on your phone. Location works here because the site is served over https.

The first version of the app is at the same address plus `classic/`.

## 4. Updating the site later

Click the file in GitHub, click the pencil icon, make the change, and commit. Or use **Add file > Upload files** to replace a file with a new version. The site updates by itself in a minute or two.

## Things to know

- **No secrets needed.** The app uses free OpenStreetMap services with no account or key.
- **The "Ask the matching agent" box** only works inside Claude. On the public site it stays hidden, and the quiz, ranking, map and tour planner all work normally.
- **Coursework is public too.** `docs/coursework/` (proposal and memo) and `journal.md` will be visible to anyone. Delete that folder before uploading if you would rather keep them private.
- **Streamlit:** this app is not a Python app, so Streamlit Community Cloud cannot run it as is. GitHub Pages hosts it free with no changes.
