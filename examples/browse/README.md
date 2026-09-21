# Pretty listings (optional)

KrazyToGo's built-in directory page is a plain list of names. That is
intentional. The official binary has no theme engine, and a `style.css`
alone cannot restyle Go's auto-generated listing.

What *does* work: put an `index.html` in the folder you are serving.
`net/http` FileServer will send that page instead of the auto list.
Link a stylesheet from there. Click a file and the browser still opens
the real image, video, or document.

These files are **examples**. Copy them onto the volume. Do not bake
them into the official scratch image.

## Use it

From the repo root, with browse left on (the default):

```bash
mkdir -p data
cp examples/browse/index.html examples/browse/style.css data/
# add your files next to them, then:
krazytogo -root ./data -addr :8080
# → http://127.0.0.1:8080/
```

Krazy Kontainer (same files, same volume):

```bash
docker run --rm -p 8080:8080 -v "$PWD/data:/data" \
  ghcr.io/crimsonflower420/krazytogo:latest
```

Edit `index.html` and point the sample cards at *your* files. Nested
folders can each have their own `index.html`, or none — folders without
one still get the built-in list.

## What this is not

- Not thumbnails. The browser shows the original file when you click it.
  Pre-generate thumbs into the volume if you want a grid of small images.
- Not a package you `apt` into the official Kontainer. The official image
  stays scratch. Helpers live in other boxes; pages live on the volume.
- Not a change to `cmd/krazytogo`. Grow the folder, not the process.
