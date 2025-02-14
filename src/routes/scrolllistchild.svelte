<script lang="ts">
	let { children, width = '100%', height = 'auto' } = $props();
</script>

<div class="scroll-container" style="width: {width}; height: {height};">
	{@render children?.()}
</div>

<style>
	.scroll-container {
		display: flex;
        flex-direction: column;
        overflow-y: auto;
		overflow-x: hidden;
		gap: 10px;
		padding: 10px;
		white-space: nowrap;
		scroll-snap-type: x mandatory;
		scrollbar-width: thin;
		/* scrollbar-color: transparent transparent; */
	}
</style>
