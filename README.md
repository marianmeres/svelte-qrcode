# @marianmeres/svelte-qrcode

[QR-Code-generator](https://github.com/nayuki/QR-Code-generator) wrapped as a Svelte component.

## Installation

```sh
npm i @marianmeres/svelte-qrcode
```

## Usage

```html
<script>
	import { QrCode } from '@marianmeres/svelte-qrcode';
</script>

<QrCode content="this will be qr encoded as svg string" />
```

See [playground](https://qr.meres.sk) for more parameters.

## SVG as a string

The same encoder is available as pure, DOM-free functions — e.g. for a server endpoint
serving `image/svg+xml`, or a file download.

```ts
import { toQrSvg, toQrPath } from '@marianmeres/svelte-qrcode/qrcodegen';

// toQrSvg(content, ecl = 'medium', border = 4, lightColor = 'white', darkColor = 'black')
const svg = toQrSvg('https://example.com', 'quartile');

// raw geometry, to build your own markup
const { size, path } = toQrPath('https://example.com', 'quartile');
```

`toQrSvg` returns a standalone SVG (with `xmlns`, `viewBox`, no `width`/`height`) which is also
valid inline in HTML. Both are re-exported from the package root too, but the
`/qrcodegen` subpath does not require a Svelte-aware bundler, so it also works in plain
Node or Deno.
