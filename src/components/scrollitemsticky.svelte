<script lang="ts">
	let { children, isSticky = false, top_offset = '0', bg_on_stick = 'white' } = $props();
</script>

<div
	class="scroll-sticky"
	class:is-sticky={isSticky}
	style=" --stickybg :{isSticky ? bg_on_stick : 'transparent'};
top: {top_offset};"
>
	{@render children?.()}
</div>

<style>
	.scroll-sticky {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		height: fit-content;
		padding: 0;
		transition: 0.3s ease-in-out;
		background-color: var(--stickybg);
	}

	.is-sticky {
		position: sticky;
		top: 0;
		left: 0;
		width: 100%;
		z-index: 1000;
		box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
	}
</style>
