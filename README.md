# Reelhouse: setup guide

Reelhouse is a movie website for content you own or have licensed. It runs on GitHub Pages (free) and plays movies from Google Drive.

Files in this folder:
- index.html: the whole website
- movies.json: your movie list (starts empty)
- movies.example.json: a full example entry to copy from
- README.md: this guide

## Part 1: Put the site online (GitHub Pages)

1. Sign in at github.com. Click the + icon (top right) > New repository.
2. Name it, for example `reelhouse`. Choose Public (free Pages needs Public unless you have a paid plan). Click Create repository.
3. Click "uploading an existing file". Drag in `index.html` and `movies.json`. Click Commit changes.
4. Go to Settings > Pages. Under "Build and deployment", set Source to "Deploy from a branch", Branch to `main`, folder `/ (root)`. Click Save.
5. Wait one to two minutes. Your site is at `https://YOUR-USERNAME.github.io/reelhouse/`. Open it to check it loads.

## Part 2: Prepare a movie in Google Drive

Only upload movies you own or have a license to stream. Pirated files can get your Drive and GitHub accounts suspended.

1. Open drive.google.com, click New > File upload, and choose your movie (.mp4 is best).
2. Wait for it to finish processing. Open the file once in Drive to confirm it plays.
3. Right-click the file > Share > under General access choose "Anyone with the link", role Viewer. Click Copy link.

## Part 3: Add the movie to the site

1. Open your site with `#admin` on the end: `https://YOUR-USERNAME.github.io/reelhouse/#admin`.
2. Fill in title, year, genre, quality and description. Cast, age rating, poster and trailer are optional.
3. Paste the Drive link into "Google Drive share link". For a second quality (for example 4K), fill in the second quality label and its Drive link.
4. Tick the rights box and tap Generate entry. A block of text appears.
5. On GitHub, open `movies.json` > click the pencil icon (Edit).
6. Paste the block between the `[` and `]`. Rules: entries are separated by commas, and the last entry has no comma after it. Example with two movies:
   ```
   [
     { ...first movie... },
     { ...second movie... }
   ]
   ```
7. Click Commit changes. After about a minute, refresh your site. The movie shows in "Recently added" and in the grid.

## Part 4: Add poster images (optional)

1. In your repo click Add file > Upload files. Create a folder by typing `posters/` before the file name, or upload the images and move them.
2. Use portrait images about 600 x 900 px, under 300 KB each (JPG).
3. The poster link is `https://YOUR-USERNAME.github.io/reelhouse/posters/FILE-NAME.jpg`. Paste it into the Poster field in the admin form.

## Part 5: Use the site features

- Search finds title, actor, director or year.
- Sort by newest, release year or A to Z. Filter by quality.
- "Recently added" shows your 8 newest movies on top.
- Each movie window has Trailer, Share, Add to watchlist, quality buttons (when you gave two), and a "More like this" row.
- Movies played from a direct video link remember where the viewer stopped. Drive's player can't do this.

## Security: who can add movies?

The #admin form only generates text. Nobody can change your site unless they have write access to your GitHub repo. Don't add collaborators you don't trust, and turn on two-factor sign-in for GitHub.

## Limits and troubleshooting

- Drive's player can show "quota exceeded" on popular files, and it is not built for large audiences. For more viewers, use a video host you're licensed on (such as Cloudflare Stream or Bunny) and paste its direct .mp4/.webm link into "direct video link".
- Movie shows a Drive error: re-check sharing is "Anyone with the link".
- Movie doesn't appear: check `movies.json` for a missing or extra comma. Paste it into jsonlint.com to find the error.
- Site shows old content: hard refresh, or wait a minute for GitHub to rebuild.
- Page is blank locally: opening index.html straight from your computer blocks movies.json. Use the GitHub Pages link.
- Custom domain (optional): Settings > Pages > Custom domain.
