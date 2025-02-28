<script lang="ts">
	interface ScrollListProps {
		numItems?: number;
		img?: string;
		itemWidth?: string;
		itemHeight?: string;
		width?: string;
		height?: string;
		scrollAmount?: number;
		descrp?: boolean;
		// playlist info
		playlist_name?: string;
		playlist_author?: string;
	}

	let {
		numItems = 5,
		img = '',
		itemWidth = '150px',
		itemHeight = '100px',
		width = '100%',
		height = 'auto',
		scrollAmount = 200,
		descrp = true,
		// playlist info
		playlist_name = 'name',
		playlist_author = 'author,author,author'
	} = $props();

	const items = Array.from({ length: numItems }, (_, i) => '');
	let scrollContainer: HTMLDivElement | null = null;

	function scrollLeft() {
		if (scrollContainer) {
			scrollContainer.scrollBy({ left: -scrollAmount, behavior: 'smooth' });
		}
	}

	function scrollRight() {
		if (scrollContainer) {
			scrollContainer.scrollBy({ left: scrollAmount, behavior: 'smooth' });
		}
	}
</script>

<div class="scroll-wrapper" style="width: {width}; height: {height};">
	<button class="scroll-btn left" onclick={scrollLeft}>
		<span class="material-icons">chevron_left</span>
	</button>

	<div bind:this={scrollContainer} class="scroll-container">
		{#each items as item}
			<div class="listcard" style="width: {itemWidth};">
				<div
					class="item"
					style="width: {itemWidth}; height: {itemHeight}; background: {img
						? `url(${img})`
						: 'red'};"
				>
					<div class="play-item">
						<button class="play-btn">
							<span class="material-icons" style="font-size: 40px;">play_circle</span>
						</button>
					</div>
				</div>
				{#if descrp}
					<div class="playlist-info">
						<span style="font-size: 18px; color: #fff;">{playlist_name}</span>
						<span style="color:grey; font-size: 12px; width:100%;">{playlist_author}</span>
					</div>
				{/if}
			</div>
		{/each}
	</div>

	<button class="scroll-btn right" onclick={scrollRight}>
		<span class="material-icons">chevron_right</span>
	</button>
</div>

<style>
	.playlist-info {
		display: flex;
		flex-direction: column;
		width: 100%;
		height: 100%;
		overflow: hidden;
		text-overflow: ellipsis;
	}
	.listcard {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: flex-start;
	}
	.scroll-wrapper {
		position: relative;
		display: flex;
		align-items: center;
		width: var(--width, 100%);
		height: var(--height, auto);
	}

	.scroll-container {
		display: flex;
		overflow-x: hidden;
		/* gap: 10px;
		padding: 10px; */
		white-space: nowrap;
		scroll-snap-type: x mandatory;
		scrollbar-width: thin;
		scrollbar-color: transparent transparent;
	}

	.scroll-btn {
		position: absolute;
		top: 50%;
		transform: translateY(-50%);
		background: rgba(0, 0, 0, 0.25);
		border: none;
		color: white;
		height: 3em;
		width: 3em;
		cursor: pointer;
		border-radius: 50%;
		opacity: 0;
		transition: opacity 0.3s ease-in-out;
		z-index: 10;
	}

	.scroll-btn.left {
		left: 10px;
	}

	.scroll-btn.right {
		right: 10px;
	}

	.scroll-wrapper:hover .scroll-btn {
		opacity: 1;
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
		transform: scale(0);
		transition: transform 0.2s ease-in-out;
	}

	.item:hover .play-item {
		transform: scale(1);
	}

	.item:hover {
		transform: scale(1.05);
	}

	.play-btn {
		background: none;
		border: none;
		color: #1edf63;
		font-size: 3.5em;
		cursor: pointer;
		transition: color 0.2s ease-in-out;
	}

	.play-btn:hover {
		color: #21f06a;
	}
</style>
