# sveltekit-example-html-to-image

[![Open in StackBlitz](https://developer.stackblitz.com/img/open_in_stackblitz.svg)](https://stackblitz.com/github/maiertech/sveltekit-example-html-to-image?file=src/routes/index.svelte)

In this example I test [html-to-image](https://github.com/bubkoo/html-to-image) for client-side image generation. Choose size and pixel ratio and then press **Render as PNG** to replace the blue div with an image.

If you run the example on a retina display and choose pixel ratio 1 the image will look blurry. Choose a higher pixel ratio and the image will look crisp.

## Tasks

- [ ] Add button to download image.
- [ ] Test if html-to-image can be run in an endpoint (with jsdom or happy-dom).
