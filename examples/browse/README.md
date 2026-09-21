# Pretty listings (optional)

KrazyToGo's built-in directory page is a plain list of names. That is intentional. The official binary has no theme engine, and a style.css alone cannot restyle Go's auto-generated listing.

What does work: put an index.html in the folder you are serving. FileServer will send that page instead of the auto list. Link a stylesheet from there. Click a file and the browser still opens the real image, video, or document.

These files are examples. Copy them onto the volume. Do not bake them into the official scratch image.

## Use it

```bash
mkdir -p data
cp examples/browse/index.html examples/browse/style.css data/
krazytogo -root ./data -addr :8080
```
