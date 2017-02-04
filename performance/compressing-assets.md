# Compressing assets
- "The fastest and best-optimized resource is a resource not sent"
- Minify scripts, HTML and CSS styles
- Enable gzip compression for them on server
- Set up cache (appropriate cache age and ETag to avoid fetching the content when it doesn't change)
- Remove unnecessary pixels for image (avoid cropping and resizing)
- Use the best appropriate image format (eg. do not use PNG for photos)
- Use JPEG-XR and WebP for the best compression results for modern browsers, provide fallback for older browsers
- Strip unnecessary information from images (eg. EXIF fields in JPEG; XML namespaces, IDs in SVG)

# Optimization tools
- [Lighthouse](https://github.com/GoogleChrome/lighthouse) - performance report, especially useful for progressive web apps
- [svgo](https://github.com/svg/svgo) - node.js tool for compressing and minifying SVGs
