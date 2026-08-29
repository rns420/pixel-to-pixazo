# Vibrant Video Creator

Clone this complete project and its already working perfectly without any issues. So run this completed project on our server.

https://github.com/theanimation616-pixel/script-to-vibrant-video.git



https://www.pixazo.ai/models/

Pixazo api key 

03178ba869a446eba82bce98a79fefc3

note:- pixazo api key is with 0 credits balance so make sure use only free ai model FLUX.1 Schnell.

https://paraloncloud.com/console api key :-



prlc_667ae9e467f065c6202fc7e12f07f575a8111b7ad906dd73

note:- paraloncloud.com api key is with 0 credits balance so make sure use only free ai models Qwen 3.8 27B Is Live: a Free, OpenAI-Compatible Vision



Issue in this GitHub repo project as below:-



The crash is because the video engine's WebAssembly file isn't being served — the CDN asset URL `/__l5e/assets-v1/.../ffmpeg-core.wasm` returns a 404 JSON error (`{"error":"not_found"}`), and ffmpeg tries to instantiate that JSON as Wasm, hence "expected magic word 00 61 73 6d, found 7b 22 65 72" (`{"er`).



The good news: a valid core Wasm already exists locally at `node_modules/@ffmpeg/core/dist/esm/ffmpeg-core.wasm`, alongside `public/ffmpeg/ffmpeg-core.esm.js`.



Remaining fix (not yet applied):

1. Copy `node_modules/@ffmpeg/core/dist/esm/ffmpeg-core.wasm` to `public/ffmpeg/ffmpeg-core.wasm` so it's served as a static file with `application/wasm` (or re-upload it via the assets CLI and regenerate `src/assets/ffmpeg-core.wasm.asset.json`, since the current pointer is stale/orphaned).

2. In `src/lib/video.ts`, drop the `wasmAsset` JSON import and use `wasmURL: await toBlobURL("/ffmpeg/ffmpeg-core.wasm", "application/wasm")`.

3. Delete the stale `src/assets/ffmpeg-core.wasm.asset.json` pointer, then reload the preview and generate a video to confirm the engine loads.



Let me know when you're ready and I'll apply these changes.

This project was built with [Lovable](https://lovable.dev).

**Live app**: https://pixel-to-pixazo.lovable.app

## Build with Lovable

Continue developing this project in the [Lovable editor](https://lovable.dev/projects/c870d301-b90b-46ea-9111-ec95d98c524d).

- **Ship faster**: describe what you want to build and Lovable handles the code.
- **Stay in sync**: every change made in Lovable is committed straight to this repository.
- **Full ownership**: this code is yours. Push to `main` on GitHub and your changes sync back into Lovable, ready for your next prompt.

## Development

Prefer working locally? You need Node.js and npm — [install with nvm](https://github.com/nvm-sh/nvm#installing-and-updating).

```sh
git clone <this-repository-url>
cd <repository-name>
npm i
npm run dev
```
