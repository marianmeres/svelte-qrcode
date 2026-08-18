<script lang="ts">
	import { toQrPath, type QrEcl } from './qrcodegen.js';

	let {
		content,
		ecl = 'medium',
		border = 4,
		bgColor = '#ffffff',
		color = '#000000'
	}: {
		content: string;
		ecl?: QrEcl;
		border?: number;
		bgColor?: string;
		color?: string;
	} = $props();

	let qr = $derived(toQrPath(content, ecl, border));
</script>

<div>
	<svg viewBox="0 0 {qr.size} {qr.size}" stroke="none" style="display: block; margin: 0;">
		<rect width="100%" height="100%" fill={bgColor} />
		<path d={qr.path} fill={color} />
	</svg>
</div>

<style>
	div {
		box-sizing: border-box;
		width: 100%;
		aspect-ratio: 1/1;
	}
</style>
