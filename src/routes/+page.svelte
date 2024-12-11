<script lang="ts">
	import QrCode from '../lib/QrCode.svelte';

	let content = $state('https://github.com/nayuki/QR-Code-generator');

	let eclNum = $state(1);
	let border = $state(4);
	let bgColor = $state('#ffffff');
	let color = $state('#000000');

	let ecl: any = $derived(['low', 'medium', 'quartile', 'high'][eclNum]);
</script>

<div class="top">
	<h1><a href="https://github.com/marianmeres/svelte-qrcode">@marianmeres/svelte-qrcode</a></h1>
	<p>
		<a href="https://github.com/nayuki/QR-Code-generator"> QR-Code-generator </a>
		wrapped as a Svelte component.
	</p>
</div>
<main>
	<textarea bind:value={content} rows="4"></textarea>

	<div class="box">
		<QrCode {content} {ecl} {border} {bgColor} {color} />
	</div>

	<div class="table-box">
		<table>
			<tbody>
				<tr>
					<th>Ecl</th>
					<td><input type="range" min="0" max="3" step="1" bind:value={eclNum} /></td>
				</tr>
				<tr>
					<th>Border</th>
					<td><input type="range" min="0" max="8" step="1" bind:value={border} /></td>
				</tr>
				<tr>
					<th>Background</th>
					<td><input type="color" bind:value={bgColor} /></td>
				</tr>
				<tr>
					<th>Color</th>
					<td><input type="color" bind:value={color} /></td>
				</tr>
			</tbody>
		</table>
	</div>

	<div class="usage">{`<!-- `}Example usage inside of a Svelte component.{` -->`}</div>
	<pre>{`<script>
  import { QrCode } from '@marianmeres/svelte-qrcode';
<script/>

<QrCode
  content="${content}"
  ecl="${ecl}"
  border="${border}"
  bgColor="${bgColor}" 
  color="${color}"
/>`}</pre>
</main>

<style>
	.top {
		width: 100%;
		max-width: 640px;
		margin: 0 auto;
		text-align: center;
		margin-bottom: 3rem;
	}
	h1 {
		font-size: 1.5rem;
		margin-bottom: 1rem;
	}
	p {
		margin-bottom: 1rem;
	}
	main {
		width: 100%;
		max-width: 500px;
		margin: 0 auto;
	}
	textarea {
		width: 100%;
		border: 0;
		padding: 0.25rem;
		resize: vertical;
	}
	.table-box {
		padding: 0 0.5rem;
	}
	table {
		width: 100%;
	}
	tr,
	td {
		padding: 0.2rem;
		text-align: left;
	}
	input {
		width: 100%;
	}
	.box {
		margin: 1rem auto;
	}
	.usage {
		margin-top: 2rem;
		background-color: #ddd;
		font-size: 0.8rem;
		padding: 0.5rem;
		color: #999;
	}
	pre {
		background-color: #ddd;
		padding: 0.5rem;
		font-size: 0.8rem;
		margin: 0;
	}
</style>
