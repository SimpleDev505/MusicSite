<script lang="ts">
	import Buttonwithtooltip from './buttonwithtooltip.svelte';

	interface ScrollListProps {
		numItems?: number;
		img?: string;
		itemWidth?: string;
		itemHeight?: string;
		width?: string;
		height?: string;
	}
	let {
		numItems = 5,
		img = '',
		itemWidth = '150px',
		itemHeight = '100px',
		width = '100%',
		height = 'auto'
	} = $props();
	const items = Array.from({ length: numItems }, (_, i) => `Item ${i + 1}`);
</script>

<div class="scroll-container" style="width: {width}; height: {height};">
	{#each items as item}
		<div
			class="item"
			style="
                width: {itemWidth}; 
                height: {itemHeight}; 
                background: {img ? `url(${img})` : 'red'};
            "
		>
			<div class="play-item">
				<Buttonwithtooltip
					icon_color="#1EDF63"
					icon_hovercolor="#21f06a"
					icon_name="play_circle"
					tooltip="Play"
					icon_size="3.5em"
				></Buttonwithtooltip>
			</div>
		</div>
	{/each}
</div>

<style>
	.scroll-container {
		display: flex;
		overflow-x: auto;
		gap: 10px;
		padding: 10px;
		white-space: nowrap;
		scroll-snap-type: x mandatory;
		scrollbar-width: thin;
	}

	.item {
		flex-shrink: 0;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		background-size: cover;
		background-position: center;
		border-radius: 8px;
		scroll-snap-align: start;
		overflow: hidden;
		transition: transform 0.2s ease-in-out;
	}
	.play-item {
		width: 100%;
		height: 100%;
		display: flex;
		justify-content: flex-end;
		align-items: flex-end;
		padding: 8px;
		transform: translateY(200px);
		transform: scale(0);
		transition: transform 0.2s ease-in-out;
	}
	.item:hover .play-item {
		transform: translateY(0);
		transform: scale(1);
	}
	.item:hover {
		transform: scale(1.05);
	}
</style>
