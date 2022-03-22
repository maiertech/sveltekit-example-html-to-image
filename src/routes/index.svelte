<script>
	import { toPng } from 'html-to-image';

	let sizes = [
		{ width: 400, height: 400, label: '400 by 400' },
		{ width: 1200, height: 675, label: '1200 by 675' }
	];
	// Selected size.
	let size = sizes[1];

	let ratios = [1, 2, 3];
	// Selected pixel ratio.
	let ratio = ratios[0];

	// Node that will be rendered as image.
	let node;

	// Image src (data URL).
	let src = '';

	// Toggle to display div with class `.image` as image.
	let displayImg = false;

	// Render as image.
	async function render() {
		src = await toPng(node, { width: size.width, height: size.height, pixelRatio: ratio });
		displayImg = true;
	}
</script>

<div class="controls">
	<label>
		Size
		<select bind:value={size} disabled={displayImg}>
			{#each sizes as size}
				<option value={size}>
					{size.label}
				</option>
			{/each}
		</select>
	</label>
	<label>
		Pixel ratio
		<select bind:value={ratio} disabled={displayImg}>
			{#each ratios as ratio}
				<option value={ratio}>
					{ratio}
				</option>
			{/each}
		</select>
	</label>
	<button on:click={render} disabled={displayImg}>Render as PNG</button>
	<button on:click={() => (displayImg = false)} disabled={!displayImg}>Undo</button>
</div>

{#if !displayImg}
	<div
		bind:this={node}
		style:width={`${size.width}px`}
		style:height={`${size.height}px`}
		class="image"
	>
		<h1>Let's test html-to-image</h1>
		<p>Press <strong>Render as PNG</strong> to replace the blue box with an image.</p>
	</div>
{/if}

<div>
	{#if displayImg}
		<img {src} width={size.width} height={size.height} alt="Generated." />
	{/if}
</div>

<style>
	.controls {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		gap: 10px;
		margin-bottom: 10px;
	}

	.image {
		box-sizing: border-box;
		background-color: lightblue;
		padding: 10px;
	}

	h1 {
		margin-top: 0;
	}
</style>
