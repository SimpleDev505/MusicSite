<script lang="ts">
	let { width = '100%', height = '2px', color = 'black', pad = '0' } = $props();
</script>

<div style="width: {width}; height: {height}; padding: {pad}; ">
	<div class="line" style="background-color: {color};"></div>
</div>

<style>
	.line {
		display: flex;
		padding: 0;
	}
</style>
