<script lang="ts">
	import Buttonwithtooltip from './buttonwithtooltip.svelte';
	import Scrolllist from './scrolllist.svelte';
	import Scrolllistchild from './scrolllistchild.svelte';
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

<div class="center-cnt">
	<!-- top -->
	<div class="center-nav">
		<button>All</button>
		<button>Music</button>
		<button>Podcasts</button>
	</div>
	<!-- ---------- -->
	<div class="center-scroll-cnt">
		<div class="center-scroll" onscroll={handle_centerscroll}>
			<div class="playlist-grp">
				<div class="playlist">
					<div class="playlist-img"></div>
					<span>Playlist</span>
				</div>
				<div class="playlist">
					<div class="playlist-img"></div>
					<span>Playlist</span>
				</div>
				<div class="playlist">
					<div class="playlist-img"></div>
					<span>Playlist</span>
				</div>
				<div class="playlist">
					<div class="playlist-img"></div>
					<span>Playlist</span>
				</div>
				<div class="playlist">
					<div class="playlist-img"></div>
					<span>Playlist</span>
				</div>
				<div class="playlist">
					<div class="playlist-img"></div>
					<span>Playlist</span>
				</div>
				<div class="playlist">
					<div class="playlist-img"></div>
					<span>Playlist</span>
				</div>
				<div class="playlist">
					<div class="playlist-img"></div>
					<span>Playlist</span>
				</div>
			</div>
			<!-- picked for you -->
			<div class="picked-for-you">
				<Scrolllistchild
					onscrolllist={() => {}}
					onscrolllistReturn={() => {}}
					width="100%"
					height="100%"
				>
					<div class="picked-card">
						<span>Picked for you</span>
						<div id="picked-song">
							<div class="picked-song-img"></div>
							<div class="picked-song-ctrls">
								<span style="color: grey; font-size: small; font-weight: 500;">Playlist</span>
								<span style="white-space: nowrap; color: white; width: 100%;">Tamil Rocking</span>
								<span
									style="overflow: hidden; text-overflow:ellipsis; font-size:  12px;color: grey; width: 100%;font-weight:normal;"
									>songdescriptionnnnnnnnnnn</span
								>
								<div class="picked-song-ctrls-button">
									<Buttonwithtooltip icon_name="play_circle" tooltip="Play"></Buttonwithtooltip>
									<Buttonwithtooltip
										icon_name="add_circle"
										tooltip="Add to playlist"
										icon_outline={true}
										icon_color="grey"
										icon_size="2.5em"
									></Buttonwithtooltip>
								</div>
							</div>
							<Scrolllist numItems={10} width="calc(100% - 16em)" height="auto" itemWidth="3em"
							></Scrolllist>
						</div>
						<div>
							<span>Recently Played</span>
							<Scrolllist
								numItems={10}
								width="40em"
								height="auto"
								itemWidth="6.5em"
								itemHeight="6em"
							></Scrolllist>
						</div>
						<div>
							<span>More Like ...</span>
							<Scrolllist
								numItems={10}
								width="40em"
								height="auto"
								itemWidth="6.5em"
								itemHeight="6em"
							></Scrolllist>
						</div>
						<div>
							<span>India's Best</span>
							<Scrolllist
								numItems={10}
								width="40em"
								height="auto"
								itemWidth="6.5em"
								itemHeight="6em"
							></Scrolllist>
						</div>
						<div>
							<span>Today Biggest hits ...</span>
							<Scrolllist
								numItems={10}
								width="40em"
								height="auto"
								itemWidth="6.5em"
								itemHeight="6em"
							></Scrolllist>
						</div>
						<div>
							<span>Jump Back in ...</span>
							<Scrolllist
								numItems={10}
								width="40em"
								height="auto"
								itemWidth="6.5em"
								itemHeight="6em"
							></Scrolllist>
						</div>
					</div>
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
							<h3>Spotify Plans</h3>
							<ul>
								<li>Premium Individual</li>
								<li>Premium Duo</li>
								<li>Premium Family</li>
								<li>Premium Student</li>
								<li>Spotify Free</li>
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
				</Scrolllistchild>
			</div>
		</div>
	</div>
</div>

<style>
	/* picked for you */
	.picked-for-you {
		display: flex;
		justify-content: flex-start;
		align-content: flex-start;
		width: 100%;
		height: 100%;
		margin-top: 20px;
		overflow: hidden;
	}
	.picked-card {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		font-size: 23px;
		font-weight: bold;
		color: #fff;
		width: 100%;
	}
	#picked-song {
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center;
		width: 100%;
		height: fit-content;
	}
	.picked-song-img {
		min-width: 8em;
		height: 100%;
		border-radius: 10px;
		background-color: red;
	}
	.picked-song-ctrls {
		margin-left: 10px;
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		justify-content: center;
		row-gap: 8px;
		margin-right: 15px;
		max-width: 8em;
	}
	.picked-song-ctrls-button {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		width: 4em;
		margin-top: 10px;
	}
	/* playlist */
	.playlist-grp {
		display: grid;
		width: 100%;
		height: 7em;
		grid-template-columns: repeat(auto-fit, minmax(min(100%/2, max(64px, 100%/5)), 1fr));
		grid-template-rows: auto;
		row-gap: 15px;
		column-gap: 15px;
		justify-content: center;
		align-items: center;
	}
	.playlist {
		display: flex;
		justify-content: flex-start;
		align-items: center;
		color: #fff;
		font-weight: bolder;
		width: 100%;
		height: 100%;
		text-align: center;
		gap: 10px;
		background-color: rgba(255, 255, 255, 0.15);
		border-radius: 5px;
		overflow: hidden;
		font-size: 14px;
	}
	.playlist-img {
		background-color: red;
		min-width: 48px;
		min-height: 48px;
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
		height: 100%;
		background: rgb(6, 89, 95);
		background: linear-gradient(
			180deg,
			rgba(6, 89, 95, 1) 0%,
			rgb(18, 18, 18) 70%,
			rgb(18, 18, 18) 100%
		);
		border-radius: 20px;
		padding: 15px 0 15px 15px;
		overflow: hidden;
	}
	.center-nav {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		width: 12em;
	}
	.center-nav button:first-child {
		background-color: white;
		color: #000;
	}
	.center-nav button {
		border-radius: 25px;
		padding: 10px 12px 10px 12px;
		width: fit-content;
		box-shadow: none;
		border: none;
		color: #fff;
		font-weight: bold;
		background-color: rgba(255, 255, 255, 0.1);
	}
	.center-scroll-cnt {
		width: 100%;
		height: fit-content;
	}
	.center-scroll {
		/* scrollbar-width: thin;
		scrollbar-color: transparent rgba(255, 255, 255, 0.4); */
		height: 60vh;
		padding: 15px 5px 15px 15px;
		/* height: calc(100vh - 8em);
		width: 100%; */
	}
	.center-footer {
		display: grid;
		grid-template-columns: repeat(5, 1fr);
		grid-template-rows: auto;
		width: 100%;
		height: 14em;
		padding: 20px;
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
