<script lang="ts">
	import Buttonwithtooltip from './buttonwithtooltip.svelte';

	let {
		sidebaropen_value = false,
		playlist_author = 'Author',
		playlist_name = 'Playlist name'
	} = $props();
	let scroll_center = $state(false);
	// window.addEventListener('scroll', () => {
	// 	if (window.innerWidth < 100) {
	// 		scroll_center = true;
	// 	} else {
	// 		scroll_center = false;
	// 	}
	// });
	function handle_centerscroll(event: Event) {
		const target = event.target as HTMLElement;
		scroll_center = target.scrollTop > 50;
		console.log(scroll_center);
	}
</script>

<div class="sidebar-playlist">
	<div class="pimg">
		<i
			class="material-symbols-outlined"
			style="font-size:25px; font-variation-settings: {"'FILL'1"}; font-weight: 300; color:#fff;"
			>play_arrow</i
		>
	</div>

	{#if sidebaropen_value == true}
		<div class="sidebar-playlist-info">
			<span style="font-weight: bold; font-size: 16px;">{playlist_name}</span>
			<span style="font-weight: normal; color: grey; font-size: 14px;"
				>Playlist.{playlist_author}</span
			>
		</div>
	{/if}
</div>

<style>
	.pimg i {
		display: none;
	}
	.sidebar-playlist:hover i {
		display: block;
	}
	.sidebar-playlist:hover {
		cursor: pointer;
		background-color: rgba(255, 255, 255, 0.1);
	}
	.sidebar-playlist:hover .pimg {
		filter: brightness(90%);
	}
	.pimg {
		min-width: 3em;
		height: 3em;
		background-color: red;
		border-radius: 5px;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.sidebar-playlist {
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center;
		width: 100%;
		height: 100%;
		padding-left: 5px;
		padding-top: 5px;
		padding-bottom: 5px;
		border-radius: 8px;
	}
	.sidebar-playlist-info {
		display: flex;
		margin-left: 10px;
		flex-direction: column;
		justify-content: center;
		align-items: flex-start;
		width: 100%;
		height: 100%;
		color: white;
	}
</style>
