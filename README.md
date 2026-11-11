# The Doom Protocol

A single-page, browser-based character chat featuring Victor von Doom. It runs **SmolLM2-360M-Instruct** locally with [Transformers.js](https://huggingface.co/docs/transformers.js), preferring WebGPU and falling back to WASM.

## Live site

After GitHub Pages is enabled, the site will be available at:

https://shalini301993.github.io/Character/

## Deploy with GitHub Pages

This repository includes a GitHub Actions workflow at `.github/workflows/pages.yml`. In GitHub:

1. Open **Settings → Pages**.
2. Under **Build and deployment**, choose **GitHub Actions** as the source.
3. Open the **Actions** tab and confirm the **Deploy to GitHub Pages** workflow completes.
4. Visit the live-site URL above. The first model load requires internet access.

## Customize Doom's voice

Edit [`character.js`](./character.js) on GitHub to change the character's voice, behavior, and response rules. The page imports this prompt when it loads.

## Browser behavior

- The page itself is static; no server or API key is required.
- The model files (several hundred MB, depending on the selected backend) are fetched from Hugging Face on first use and cached by the browser where supported.
- WebGPU is attempted first. If it is unavailable or fails to initialize, the app attempts WASM.
- Conversations are generated in the browser. The app does not send chat text to an AI inference server.
- Browser storage may be cleared by the user or browser, requiring model files to be fetched again.
- Performance and memory requirements vary by device and browser. A modern desktop browser is recommended.

## Development

For local testing, serve the repository over localhost (for example, with `python -m http.server 8000`) and open http://localhost:8000. Opening the HTML directly as a `file://` URL may prevent module loading.
