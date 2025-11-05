How to download Comfortaa font files locally

This repository references local font files at `assets/fonts/Comfortaa-Regular.woff2` and `assets/fonts/Comfortaa-Bold.woff2`.

Run the following commands in your terminal to download the recommended woff2 files from Google Fonts and save them into `assets/fonts/`.

These commands fetch the Google Fonts CSS for Comfortaa, extract the woff2 URLs, and download them into the folder.

Run from the repository root (`/Users/krystaltorres/student`):

```bash
mkdir -p assets/fonts
curl -s "https://fonts.googleapis.com/css2?family=Comfortaa:wght@400;700&display=swap" \
  | grep -o 'https://fonts.gstatic.com[^)\"]*' \
  | xargs -n1 -I{} sh -c 'url="{}"; name=$(basename "$url"); echo "Downloading $name"; curl -L -o "assets/fonts/$name" "$url"'

# After this, rename the downloaded files to the expected names (if necessary):
# e.g. mv assets/fonts/comfortaa-regular-xxxx.woff2 assets/fonts/Comfortaa-Regular.woff2
# e.g. mv assets/fonts/comfortaa-700-xxxx.woff2 assets/fonts/Comfortaa-Bold.woff2
```

Notes:
- The CSS-fetch step extracts direct woff2 links used by Google Fonts. The downloaded filenames often include hash strings; rename them to the simple names used by the post (Comfortaa-Regular.woff2, Comfortaa-Bold.woff2) for convenience.
- If you prefer manual download, visit https://fonts.google.com/specimen/Comfortaa, choose the weights (Regular 400, Bold 700), and download the webfont files; then place the resulting .woff2 files into `assets/fonts/` and rename as above.
- If you want the fonts checked into the repo, add the files to git: `git add assets/fonts/*.woff2 && git commit -m "Add Comfortaa fonts"`.
