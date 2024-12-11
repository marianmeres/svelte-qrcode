<script lang="ts">
	import { toQrSvg } from './qrcodegen.js';

	let {
		content,
		ecl = 'medium',
		border = 4,
		bgColor = '#ffffff',
		color = '#000000'
	}: {
		content: string;
		ecl?: 'low' | 'medium' | 'quartile' | 'high';
		border?: number;
		bgColor?: string;
		color?: string;
	} = $props();
</script>

<div>
	{@html toQrSvg(content, ecl, border, bgColor, color)}
</div>

<style>
	div {
		box-sizing: border-box;
		width: 100%;
		aspect-ratio: 1/1;
	}
</style>
