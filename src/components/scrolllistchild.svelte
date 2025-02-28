<script lang="ts">
	let {
		children,
		width = '100%',
		height = 'auto',
		scroll_visible = true,
		items_Rowgap = '10px',
		items_Colgap = '10px',
		onscrolllist,
		onscrolllistReturn,
		scrolldepth = 100,
		pad = '10px'
	} = $props();

	function handleScroll(event: Event) {
		const target = event.target as HTMLElement;
		const scrolled = target.scrollTop;
		if (scrolled >= scrolldepth) {
			onscrolllist?.(scrolled);
		} else if (scrolled <= 0) {
			onscrolllistReturn?.();
		}
	}
</script>

<div
	class="scroll-container"
	onscroll={handleScroll}
	style="--pad :{pad}; width: {width}; height: {height}; scrollbar-color:{!scroll_visible
		? 'transparent transparent'
		: 'grey grey'}; row-gap:{items_Rowgap}; column-gap:{items_Colgap};}"
>
	{@render children?.()}
</div>

<style>
	.scroll-container {
		display: flex;
		flex-direction: column;
		overflow-y: auto;
		overflow-x: hidden;
		white-space: nowrap;
		scroll-snap-type: x mandatory;
		scrollbar-width: thin;
		padding: var(--pad);
		/* scrollbar-color: transparent transparent; */
	}
</style>
