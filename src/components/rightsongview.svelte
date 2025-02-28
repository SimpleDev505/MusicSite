<script lang="ts">
	import Buttonwithtooltip from './buttonwithtooltip.svelte';
	import Dropcomp from './dropcomp.svelte';
	import Dropdividercomp from './dropdividercomp.svelte';
	import DropItemComp from './dropitemcomp.svelte';
	import Scrollitemsticky from './scrollitemsticky.svelte';
	import Scrolllistchild from './scrolllistchild.svelte';

	let scroll_center = $state(false);
	let scroll_playlist = $state(false);
	let next_song_hover = $state(false);
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
	function scrollplaylist() {
		scroll_playlist = true;
		console.log('playlist scroll' + scroll_playlist);
	}
	function scrollplaylistReturn() {
		scroll_playlist = false;
		console.log('playlist scroll' + scroll_playlist);
	}
	interface c {
		author: string;
		role: string;
	}
	let {
		song_name = 'Song Name Song Name',
		author_name = 'Author Name Author Name Author Name Author Name',

		song_name_next = 'Next song name name',
		author_name_next = 'Next Author name name',
		credits
	} = $props<{ song_name?: string; author_name?: string; credits: c[] }>();
</script>

<div class="right-cnt">
	<Scrolllistchild
		onscrolllist={scrollplaylist}
		scroll_visible={false}
		width="100%"
		height="80vh"
		scrolldepth={100}
		pad="0 0 15px 0"
		onscrolllistReturn={scrollplaylistReturn}
	>
		<Scrollitemsticky top_offset="-1px" isSticky={scroll_playlist} bg_on_stick="#121212">
			<div class="right-top">
				<span style="color: #fff;font-weight:bold">Song Name</span>
				<div
					style="display: flex; justify-content: center; align-items: center;  flex-direction: row; width: fit-content; height: 100%;"
				>
					<Buttonwithtooltip
						icon_name="close"
						tooltip="Close"
						icon_outline={true}
						icon_color="rgba(255,255,255,.6)"
						icon_size="1.8em"
					></Buttonwithtooltip>
					<Dropcomp
						gap={0}
						contentWidth="195px"
						contentHeight="auto"
						contentBgColor="#282828"
						showIcon={true}
						icon="close"
						contentTextColor="#fff"
						contentFontWeight="400"
						contentTextGap="10px"
						contentOverallGap="4px"
						contentBorderRadius="6px"
					>
						<span slot="trigger">
							<button class="nav-home-button" style="background-color: transparent; border: none;">
								<i class="material-icons" style="color: grey;font-weight:400;">more_horiz</i>
							</button>
						</span>
						<div
							slot="content"
							style="display: flex; height: fit-content; flex-direction: column; justify-content: left; align-items: left;"
						>
							<DropItemComp>
								<p
									style="display: flex; width: 100%; align-items: center; justify-content: space-between; margin-left: 8px;"
								>
									<a href="/account" style="color: #fff; text-decoration: none;">Add to Playlists</a
									>
									<i class="material-symbols-outlined" style="font-weight: 10;">add</i>
								</p>
							</DropItemComp>
							<DropItemComp>
								<p
									style="display: flex; width: 100%; align-items: center; justify-content: space-between; margin-left: 8px;"
								>
									<a href="/user" style="color: #fff; text-decoration: none;">Save to Liked Songs</a
									>
									<i class="material-symbols-outlined" style="font-weight: 10;"
										>add_circle_outline</i
									>
								</p>
							</DropItemComp>
							<DropItemComp>
								<p
									style="display: flex; width: 100%; align-items: center; justify-content: space-between; margin-left: 8px;"
								>
									<a href="/premium" style="color: #fff; text-decoration: none;">Add to Queue</a>
									<i class="material-symbols-outlined" style="font-weight: 10;">queue_music</i>
								</p>
							</DropItemComp>
							<Dropdividercomp width="100%" height="1px" color="#8D8D93" padding="0" />
							<DropItemComp>
								<p
									style="display: flex; width: 100%; align-items: center; justify-content: space-between; margin-left: 8px;"
								>
									<a href="/songradio" style="color: #fff; text-decoration: none;"
										>Go to Song Radio</a
									>
									<i class="material-symbols-outlined" style="font-weight: 10;">radar</i>
								</p>
							</DropItemComp>
							<DropItemComp>
								<p
									style="display: flex; width: 100%; align-items: center; justify-content: space-between; margin-left: 8px;"
								>
									<a href="/download" style="color: #fff; text-decoration: none;">Go to Artist</a>
									<i class="material-symbols-outlined" style="font-weight: 10;">person</i>
								</p>
							</DropItemComp>
							<DropItemComp>
								<p
									style="display: flex; width: 100%; align-items: center; justify-content: space-between; margin-left: 8px;"
								>
									<a href="/album" style="color: #fff; text-decoration: none;">Go to Album</a>
									<i class="material-symbols-outlined" style="font-weight: 10;">adjust</i>
								</p>
							</DropItemComp>
							<DropItemComp>
								<p
									style="display: flex; width: 100%; align-items: center; justify-content: space-between; margin-left: 8px;"
								>
									<a href="/credits" style="color: #fff; text-decoration: none;">View Credits</a>
									<i class="material-symbols-outlined" style="font-weight: 10;">menu</i>
								</p>
							</DropItemComp>
							<Dropdividercomp width="100%" height="1px" color="#8D8D93" padding="0" />
							<DropItemComp>
								<p
									style="display: flex; width: 100%; align-items: center; justify-content: space-between; margin-left: 8px;"
								>
									<a href="/settings" style="color: #fff; text-decoration: none;">Share</a>
									<i class="material-symbols-outlined" style="font-weight: 10;">share</i>
								</p>
							</DropItemComp>
							<Dropdividercomp width="100%" height="1px" color="#8D8D93" padding="0" />
							<DropItemComp>
								<p
									style="display: flex; align-items: center; justify-content: space-between; margin-left: 8px;"
								>
									<a href="/appdownload" style="color: #fff; text-decoration: none;"
										>Open in Desktop App</a
									>
									<button
										class="nav-home-button"
										style="background-color: #fff;width:fit-content; height: 2em; margin-left: 25px; border-radius: 25px;
									display: flex; justify-content: center; align-items: center;"
										><i
											class="material-symbols-outlined"
											style="font-weight: 300; color: black;font-size:1.5em;">music_cast</i
										></button
									>
								</p>
							</DropItemComp>
						</div>
					</Dropcomp>
				</div>
			</div>
		</Scrollitemsticky>

		<div
			class="song_img
		"
		></div>
		<div class="song_info">
			<span style="font-size: 2.5em; font-weight: bold;">{song_name}</span>
			<span style="font-size: 1.5em;">{author_name}</span>
		</div>
		<div class="Credits">
			<div class="credits-top">
				<span>Credits</span>
				<span style="color: grey;">ShowAll</span>
			</div>
			<div class="credits-cnt">
				{#each credits as c}
					<div class="credits-to">
						<div class="credits-to-info">
							<span>{c.author}</span>
							<span style="font-weight: normal; color: grey; font-size: 1em;">{c.role}</span>
						</div>
						<button>Follow</button>
					</div>
				{/each}
			</div>
		</div>
		<div class="next-song">
			<div class="credits-top">
				<span>Next</span>
				<span style="color: grey;">Open queue</span>
			</div>
			<div class={next_song_hover ? 'next-song-info next-song-info-hover' : 'next-song-info'}>
				<div class="next-song-img">
					<i
						class="material-symbols-outlined"
						style=" width:fit-content;font-size:26px; font-variation-settings: {"'FILL'1"}; font-weight: 300; color:#fff;"
						>play_arrow</i
					>
				</div>
				<div class="next-song-cnt">
					<span>{song_name_next}</span>
					<span style="color: grey; font-size: .8em;">{author_name_next}</span>
				</div>
			</div>
		</div>
	</Scrolllistchild>
</div>

<style>
	.next-song-info-hover {
		background-color: #252525;
	}
	.next-song-cnt {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: flex-start;
		width: fit-content;
		height: 100%;
		margin-left: 15px;
		font-weight: bold;
	}
	.next-song-img {
		display: flex;
		justify-content: center;
		align-items: center;
		background-color: red;
		height: 3.5em;
		width: 3.5em;
		border-radius: 5px;
	}
	.next-song-info {
		margin-top: 5px;
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center;
		width: 100%;
		height: 100%;
	}
	.next-song {
		display: flex;
		flex-direction: column;
		width: 100%;
		min-height: 7em;
		color: #fff;
		background-color: #252525;
		border-radius: 10px;
		padding: 12px;
	}
	/* next */
	.credits-to-info {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		width: fit-content;
		height: 2.5em;
	}
	.credits-to {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		width: 100%;
		height: fit-content;
		margin-top: 15px;
	}
	.credits-to button {
		background-color: transparent;
		border: 1px solid rgba(255, 255, 255, 0.5);
		color: #fff;
		padding: 5px;
		padding-left: 15px;
		padding-right: 15px;
		border-radius: 25px;
		font-size: 1em;
		transition: 0.1s ease-in-out;
	}
	.credits-to button:hover {
		scale: 1.1;
		border: 1px solid white;
		cursor: pointer;
	}
	.credits-cnt {
		margin-top: 15px;
		display: flex;
		flex-direction: column;
		width: 100%;
		height: 100%;
		color: #fff;
		font-weight: 550;
		align-items: flex-start;
	}
	.Credits {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: flex-start;
		width: 100%;
		min-height: 15em;
		background-color: #252525;
		padding: 25px;
		border-radius: 10px;
	}
	.credits-top {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: flex-start;
		width: 100%;
		height: fit-content;
		color: #fff;
		font-weight: bold;
	}
	/* credits */
	.song_info {
		display: flex;
		flex-direction: column;
		width: 100%;
		min-height: fit-content;
		color: #fff;
		text-overflow: ellipsis;
		overflow-x: hidden;
		overflow-y: hidden;
	}
	.song_img {
		display: flex;
		width: 25em;
		min-height: 25em;
		background-color: red;
		border-radius: 15px;
	}
	/* right */
	.right-cnt {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-items: flex-start;
		width: 28em;
		height: 100%;
		padding: 20px;
	}
	.right-top {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		width: 100%;
		height: 4em;
	}
</style>
