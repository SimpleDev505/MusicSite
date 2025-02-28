<script lang="ts">
	import Buttonwithtooltip from './buttonwithtooltip.svelte';
	import Scrolllistchild from './scrolllistchild.svelte';
	import Playlistcard from './playlistcard.svelte';
	import Scrollitemsticky from './scrollitemsticky.svelte';
	let scroll_center = $state(false);
	let scroll_playlist = $state(false);
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

	let {
		playlist_name = 'Latest Song',
		latest_updated_song_name = 'latest put song name',
		playlist_saves = '9999999',
		playlist_amount_songs = '10',
		playlist_total_listen_time = '3hr'
	} = $props();
	function scrollplaylist() {
		scroll_playlist = true;
		console.log('playlist scroll' + scroll_playlist);
	}
	function scrollplaylistReturn() {
		scroll_playlist = false;
		console.log('playlist scroll' + scroll_playlist);
	}
</script>

<div class="center-cnt">
	<!-- top -->
	<Scrolllistchild
		onscrolllist={scrollplaylist}
		scroll_visible={false}
		width="100%"
		height="80vh"
		scrolldepth={100}
		pad="0px"
		onscrolllistReturn={scrollplaylistReturn}
	>
		<div id="center-nav">
			<span class="playlist-img"></span>
			<div class="playlist-info">
				<span>Playlist</span>
				<span style="font-size: 4em;font-weight:600;">{playlist_name}</span>
				<span style="font-size: .9em; color: #d9d9d7;font-weight:500;"
					>New Music From Kollywood.Cover {latest_updated_song_name}</span
				>
				<div class="playlist-info-descrp" style="font-weight:500;">
					<span>{playlist_saves} saves</span>
					<span>.</span>
					<span>{playlist_amount_songs} songs</span>
					<span>,</span>
					<span>about {playlist_total_listen_time}</span>
				</div>
			</div>
		</div>

		<!-- ---------- -->
		<div class="center-scroll-cnt">
			<Scrollitemsticky isSticky={scroll_playlist} top_offset="-1px" bg_on_stick="#434343">
				<div class="playlist-ctrls">
					<Buttonwithtooltip
						icon_name="play_circle"
						icon_color="#1ED760"
						icon_size="4.5em"
						tooltip_pos="translate(5px,-25px)"
						tooltip="Play"
					></Buttonwithtooltip>
					{#if scroll_playlist == false}
						<Buttonwithtooltip
							icon_name="add_circle"
							tooltip="Add to playlist"
							icon_outline={true}
							icon_color="rgba(255,255,255,.6)"
							icon_size="2.5em"
						></Buttonwithtooltip>
						<Buttonwithtooltip
							icon_name="more_horiz"
							tooltip="More options"
							icon_outline={true}
							icon_color="rgba(255,255,255,.6)"
							icon_size="2.25em"
						></Buttonwithtooltip>
					{:else}
						<span style=" color: #fff; font-size: 1.5em;font-weight:600;">{playlist_name}</span>
					{/if}
				</div>
			</Scrollitemsticky>
			<Scrollitemsticky isSticky={scroll_playlist} top_offset="68px" bg_on_stick="#1F1F1F">
				<div class="playlist-layout-info">
					<span>#</span>
					<span style="width: 14em;">Title</span>
					<span style="width: 10em;">Album</span>
					<span>Date Added</span>
					<span
						class="material-symbols-outlined"
						style="font-weight: 250; color: rgba(255,255,255,.5);"
					>
						schedule
					</span>
				</div>
			</Scrollitemsticky>

			<div class="center-scroll" onscroll={handle_centerscroll}>
				<!-- picked for you -->
				<div class="picked-for-you">
					<div
						style="width: 97%; height: 1px; margin: auto; background-color: grey; margin-top: 8px;"
					></div>

					<Playlistcard></Playlistcard>
					<Playlistcard></Playlistcard>
					<Playlistcard></Playlistcard>
					<Playlistcard></Playlistcard>
					<Playlistcard></Playlistcard>
					<Playlistcard></Playlistcard>
					<Playlistcard></Playlistcard>
					<Playlistcard></Playlistcard>
					<Playlistcard></Playlistcard>
					<Playlistcard></Playlistcard>
					<Playlistcard></Playlistcard>
					<Playlistcard></Playlistcard>
					<!-- footer -->
					<div class="center-footer">
						<div class="center-footer-cnt">
							<h3>Company</h3>
							<ul>
								<li>About</li>
								<li>Jobs</li>
								<li>For the Record</li>
							</ul>
						</div>
						<div class="center-footer-cnt">
							<h3>Communities</h3>
							<ul>
								<li>For Artists</li>
								<li>Developers</li>
								<li>Advertising</li>
								<li>Investors</li>
								<li>Vendors</li>
							</ul>
						</div>
						<div class="center-footer-cnt">
							<h3>Useful Links</h3>
							<ul>
								<li>Support</li>
								<li>Free Mobile App</li>
							</ul>
						</div>
						<div class="center-footer-cnt">
							<h3>Plans</h3>
							<ul>
								<li>Premium Individual</li>
								<li>Premium Duo</li>
								<li>Premium Family</li>
								<li>Premium Student</li>
								<li>Free</li>
							</ul>
						</div>
						<div class="center-footer-cnt-socials">
							<ul>
								<li>
									<img
										src="https://img.icons8.com/?size=100&id=85154&format=png&color=ffffff"
										alt="social-icons"
									/>
								</li>
								<li>
									<img
										src="https://img.icons8.com/?size=100&id=fJp7hepMryiw&format=png&color=ffffff"
										alt="social-icons"
									/>
								</li>
								<li>
									<img
										src="https://img.icons8.com/?size=100&id=118467&format=png&color=ffffff"
										alt="social-icons"
									/>
								</li>
							</ul>
						</div>
					</div>
				</div>
			</div>
		</div>
	</Scrolllistchild>
</div>

<style>
	.playlist-layout-info {
		display: grid;
		grid-template-columns: auto 1fr 1fr 1fr auto;
		grid-template-rows: auto 1fr 1fr 1fr 1fr;
		justify-content: flex-start;
		align-items: center;
		padding-top: 15px;
		padding-left: 35px;
		padding-right: 35px;
		width: 100%;
		color: rgba(255, 255, 255, 0.5);
		column-gap: 20px;
		background-color: transparent;
		/* background-color: #353535; */
	}
	.playlist-layout-info span {
		display: flex;
		width: 100%;
	}
	/* picked for you */
	.picked-for-you {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-content: flex-start;
		width: 100%;
		height: 100%;
		margin-top: 20px;
		overflow: hidden;
		background-color: none;
	}
	.playlist-ctrls {
		display: flex;
		flex-direction: row;
		width: 100%;
		justify-content: flex-start;
		column-gap: 1em;
		align-items: center;
		padding-top: 10px;
		padding-left: 15px;
		padding-right: 15px;
		background-color: transparent;
		/* background-color: #353535; */
	}
	/* playlist */
	.playlist-img {
		background-color: red;
		min-width: 13em;
		min-height: 13em;
		border-radius: 8px;
		-webkit-box-shadow: 10px 10px 127px -44px rgba(0, 0, 0, 0.75);
		-moz-box-shadow: 10px 10px 127px -44px rgba(0, 0, 0, 0.75);
		box-shadow: 10px 10px 127px -44px rgba(0, 0, 0, 0.75);
	}
	.playlist-info {
		margin-top: 25px;
		display: flex;
		flex-direction: column;
		row-gap: 15px;
		color: #fff;
		margin-left: 15px;
		width: 100%;
		container-name: playlistInfo;
	}
	@container playlistInfo (min-width: 25%) {
	}
	.playlist-info-descrp {
		color: #d9d9d7;
	}
	/* right */

	/* -------------- */
	/* Center */
	.center-cnt {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-content: flex-start;
		width: 100%;
		height: fit-content;
		background: rgb(111, 111, 111);
		background: linear-gradient(
			180deg,
			rgba(111, 111, 111, 1) 0%,
			rgba(176, 176, 176, 1) 50%,
			rgba(255, 255, 255, 1) 100%
		);
		border-radius: 20px;
		padding: 0px;
		/* padding: 15px 0 0 0; */
		overflow: hidden;
	}
	#center-nav {
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center;
		width: 100%;
		height: fit-content;
		padding-top: 10px;
		padding-left: 15px;
		padding-right: 15px;
	}

	.center-scroll-cnt {
		display: flex;
		flex-direction: column;
		width: 100%;
		height: fit-content;
		background-color: #121212;
	}
	.center-scroll {
		display: flex;
		flex-direction: column;
		/* scrollbar-width: thin;
		scrollbar-color: transparent rgba(255, 255, 255, 0.4); */
		height: fit-content;
		/* padding: 5px 5px 15px 15px; */
		/* height: calc(100vh - 8em);
		width: 100%; */
	}
	.center-footer {
		display: grid;
		grid-template-columns: repeat(5, 1fr);
		grid-template-rows: auto;
		width: 100%;
		height: 15em;
		padding: 20px;
		margin-bottom: 15px;
		background-color: transparent;
	}
	.center-footer-cnt {
		padding: 10px;
		width: 100%;
		height: 100%;
		font-size: 16px;
		font-weight: normal;
		color: #fff;
	}
	.center-footer-cnt ul {
		padding: 0;
		list-style: none;
		text-decoration: none;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: flex-start;
		row-gap: 10px;
		color: grey;
	}
	.center-footer-cnt-socials ul {
		padding: 0;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		height: 50%;
		column-gap: 10px;
	}
	.center-footer-cnt-socials li {
		display: block;
	}
	.center-footer-cnt-socials li:hover {
		cursor: pointer;
	}
	.center-footer-cnt ul li:hover {
		text-decoration: underline white 1px;
		color: #fff;
		cursor: pointer;
	}
	.center-footer-cnt-socials img {
		background-color: #292929;
		padding: 10px;
		border-radius: 20px;
		width: 2.4em;
		height: 2.4em;
	}
	.center-footer-cnt-socials img:hover {
		background-color: #353535;
		scale: 1.1;
	}
</style>
