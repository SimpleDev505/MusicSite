<script lang="ts">
	let {
		listid = 0,
		imgurl = '',
		song_name = 'SONG NAME SONG NAME',
		author_name = 'AUTHOR NAME AUTHOR NAME',
		date_added = '2',
		duration = '4:21'
	} = $props();

	let cardhovered = $state(false);
</script>

<div
	class="playlist-card"
	onpointerenter={() => (cardhovered = true)}
	onpointerleave={() => (cardhovered = false)}
>
	{#if cardhovered}
		<i
			class="material-symbols-outlined"
			style="width:10px;font-size:22px; font-variation-settings: {"'FILL'1"}; font-weight: 300; color:#fff;"
			>play_arrow</i
		>
	{:else}
		<div style="width: 10px;">{listid}</div>
	{/if}
	<div class="playlist-card-cnt">
		<div class="playlist-card-img" style="--img:{listid}"></div>
		<div class="playlist-card-cnt-info">
			<div
				class="playlist-card-song"
				style="color: #fff; font-weight: bold; font-size: 16px; width: 10em; text-overflow: ellipsis; overflow-x: hidden;"
			>
				{song_name}
			</div>
			<div
				class="playlist-card-author"
				style="font-size: 14px; width: 10em; overflow-x: hidden; text-overflow: ellipsis;"
			>
				{author_name}
			</div>
		</div>
	</div>
	<div style="font-size: 14px;">{song_name}</div>
	<div>{date_added} days ago</div>
	<div>{duration}</div>
</div>

<style>
	.playlist-card:hover {
		background-color: rgba(255, 255, 255, 0.1);
		border-radius: 8px;
	}
	.playlist-card-cnt {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		width: 100%;
		height: 100%;
	}
	.playlist-card-cnt-info {
		margin-left: 8px;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: flex-start;
		width: 100%;
		height: 100%;
	}
	.playlist-card {
		display: grid;
		grid-template-columns: auto 1fr 1fr 1fr auto;
		grid-template-rows: auto 1fr 1fr 1fr 1fr;
		justify-content: flex-start;
		align-items: center;
		padding-top: 10px;
		padding-bottom: 10px;
		padding-left: 35px;
		padding-right: clamp(100px, 100%, 30px);
		width: 100%;
		height: 4em;
		column-gap: 20px;
		color: rgb(176, 175, 175);
		cursor: pointer;
	}
	.playlist-card-img {
		min-width: 3em;
		min-height: 3em;
		background-color: red;
		border-radius: 5px;
	}
</style>
