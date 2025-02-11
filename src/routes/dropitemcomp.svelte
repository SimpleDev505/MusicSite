<script lang="ts">
	export let ht: string = '2.5em';
	export let hoverBg: string = '#3E3E3E'; // background color when hovered
</script>

<div class="dropdown-item" style="--hover-bg: {hoverBg}; --ht:{ht};">
	<slot></slot>
</div>

<style>
	.dropdown-item {
		display: flex;
		justify-content: left;
		align-items: center;
		transition: background-color 0.2s ease;
		height: var(--ht);
		box-sizing: border-box;
		width: 100%;
	}
	.dropdown-item:hover {
		background-color: var(--hover-bg);
	}
</style>
