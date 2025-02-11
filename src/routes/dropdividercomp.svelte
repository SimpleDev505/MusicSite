<script lang="ts">
	// Adjustable parameters for the divider.
	export let width: string = '100%';
	export let height: string = '1px';
	export let color: string = '#ccc';
	export let padding: string = '0.5rem 0';
</script>

<div
	class="dropdown-divider"
	style="width: {width}; height: {height}; background-color: {color}; padding: {padding};"
></div>

<style>
	.dropdown-divider {
		box-sizing: border-box;
	}
</style>
