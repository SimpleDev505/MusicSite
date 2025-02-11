<script>
	import Buttonwithtooltip from './buttonwithtooltip.svelte';
	import Navbar from './navbar.svelte';
	import Progresscomp from './progresscomp.svelte';
	import Scrolllist from './scrolllist.svelte';
	let sidebaropen = $state(false);
	let controls_over = $state(false);
</script>

<div class="home-layout">
	<div class="navc"><Navbar /></div>
	<div class="left">
		<!-- nav left -->
		<div class="sidebar-left {sidebaropen ? 'sidebar-open' : ''}">
			<button
				class="sidebar-icon"
				style="background-color: transparent; border: none;"
				onclick={() => {
					console.log(sidebaropen);
					sidebaropen ? (sidebaropen = false) : (sidebaropen = true);
				}}
			>
				<i class="material-symbols-outlined" style="font-weight: 10;">right_panel_close</i>
			</button>
			<div class="sidebar-cnt">
				<div class="sidebar-cnt-items">
					<div></div>
					<div></div>
					<div></div>
					<div></div>
					<div></div>
					<div></div>
					<div></div>
					<div></div>
					<div></div>
				</div>
			</div>
		</div>
	</div>
	<div class="center">
		<div class="center-cnt">
			<div class="center-nav">
				<button>All</button>
				<button>Music</button>
				<button>Podcasts</button>
			</div>
			<div class="center-scroll">
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
							<Scrolllist numItems={10} width="27em" height="auto" itemWidth="3em"></Scrolllist>
						</div>
						<div>
							<span>Recently Played</span>
							<Scrolllist numItems={10} width="40em" height="auto" itemWidth="6.5em" itemHeight="6em"
							></Scrolllist>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
	<div class="right">
		<div class="right-cnt">
			<span style="color: #fff;font-weight:bold">Song Name</span>
			<div class="song-cover-img"></div>
		</div>
	</div>
	<div class="bnav">
		<!-- left -->
		<div class="bnav-left">
			<div class="playingsong-img"></div>
			<div class="playingsong-info">
				<span style="font-weight: 600; font-size: 1em;">Song Name</span>
				<span
					id="Artist-Names"
					style="font-weight: normal; font-size: .7em; color:grey; width: 25em;"
					>Name,Name,Name,Name,Name,Name,Name,Name,Name,Name,Name,Name,Name,</span
				>
			</div>
			<div id="addtoplaylist">
				<i
					class="material-symbols-outlined"
					style="font-variation-settings: {"'FILL'1"}; font-weight: 300;">verified</i
				>
			</div>
		</div>
		<!-- center -->
		<div class="bnav-center">
			<div class="songplay-controls">
				<Buttonwithtooltip
					icon_color="grey"
					tooltip_pos="translate(-25px,-25px)"
					icon_name="shuffle"
					tooltip="Shuffle"
					icon_size="1.5em"
					b_class="player-control"
				></Buttonwithtooltip>
				<Buttonwithtooltip
					icon_color="grey"
					tooltip_pos="translate(-25px,-25px)"
					icon_name="fast_forward"
					tooltip="Previous"
					icon_size="1.8em"
					b_class="player-control"
					inv_icon={true}
				></Buttonwithtooltip>

				<Buttonwithtooltip icon_name="play_circle" tooltip="Play"></Buttonwithtooltip>
				<Buttonwithtooltip
					icon_name="fast_forward"
					tooltip="Next"
					icon_color="grey"
					icon_size="1.8em"
				></Buttonwithtooltip>
				<Buttonwithtooltip
					icon_color="grey"
					tooltip_pos="translate(-25px,-25px)"
					icon_name="laps"
					tooltip="Repeat"
					icon_outline={true}
					icon_size="1.5em"
					b_class="player-control"
					inv_icon={true}
				></Buttonwithtooltip>
			</div>
			<div class="songplay-timing">
				<span>0:00</span>
				<Progresscomp backgroundColor="grey" height="4px" fillColor="#fff" progress={10} />
				<span>3:00</span>
			</div>
		</div>
		<div class="bnav-right">
			<button>
				<div
					class="tooltip"
					style="padding: 10px; justify-content: center; align-items: center;  background-color: #3E3E3E ; width:fit-content; z-index: 1000; height:15px; color: #fff; position: absolute; transform: translate(-15px,-25px);"
				>
					Lyrics
				</div>
				<i class="material-icons" style="font-size: 1.5em;"> mic</i></button
			>
			<button>
				<div
					class="tooltip"
					style="padding: 10px; justify-content: center; align-items: center; width:fit-content; z-index: 1000; height:15px; color: #fff; position: absolute; transform: translate(-15px,-25px); "
				>
					Queue
				</div>
				<i class="material-icons" style="font-size: 1.5em;">queue_music</i></button
			>
			<button>
				<div
					class="tooltip"
					style="padding: 10px; justify-content: center; align-items: center; width:fit-content; z-index: 1000; height:15px; color: #fff; position: absolute; transform: translate(-15px,-25px); "
				>
					Connect
				</div>
				<i class="material-icons {controls_over ? 'controls-over' : ' '} " style="font-size: 1.5em;"
					>cast</i
				>
			</button>
			<div id="volume-control">
				<button>
					<div
						class="tooltip"
						style="padding: 10px; justify-content: center; align-items: center; width:fit-content; z-index: 1000; height:15px; color: #fff; position: absolute; transform: translate(-15px,-25px); "
					>
						Volume
					</div>
					<i class="material-icons" style="font-size: 1.5em;"> volume_down</i></button
				>
				<Progresscomp backgroundColor="grey" height="4px" fillColor="#fff" progress={10} />
			</div>
			<button>
				<div
					class="tooltip"
					style="padding: 10px; justify-content: center; align-items: center; width:fit-content; z-index: 1000; height:15px; color: #fff; position: absolute; transform: translate(-15px,-25px); "
				>
					MiniPlayer
				</div>
				<i class="material-icons" style="font-size: 1.5em;">featured_play_list</i></button
			>
			<button>
				<div
					class="tooltip"
					style="padding: 10px; justify-content: center; align-items: center; width:fit-content; z-index: 1000; height:15px; color: #fff; position: absolute; transform: translate(-75px,-25px); "
				>
					Fullscreen
				</div>
				<i class="material-icons" style="font-size: 1.5em;">open_in_full</i></button
			>
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
		padding: 12px;
		margin-top: 20px;
		overflow: hidden;
	}
	.picked-card {
		display: flex;
		flex-direction: column;
		justify-content: space-evenly;
		align-items: flex-start;
		font-size: 23px;
		font-weight: bold;
		color: #fff;
		width: 100%;
		height: 100%;
	}
	#picked-song {
		margin-top: 15px;
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center;
		width: 100%;
		overflow-x: hidden;
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
		overflow: hidden;
		row-gap: 8px;
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
	.right-cnt {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-items: flex-start;
		width: 25em;
		height: 100%;
		padding: 20px;
	}
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
		background: linear-gradient(180deg, rgba(6, 89, 95, 1) 0%, rgb(0, 0, 0) 100%);
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
	.center-scroll {
		overflow-y: scroll;
		scrollbar-width: thin;
		scrollbar-color: transparent rgba(255, 255, 255, 0.4);
		height: 100%;
		width: 100%;
		padding: 15px 5px 15px 15px;
	}
	/* -------- */
	#Artist-Names {
		overflow: hidden;
		text-overflow: ellipsis;
	}
	/* ---------- */
	/* right */
	.bnav-right {
		display: flex;
		justify-content: flex-end;
		align-items: center;
		width: 35em;
		height: fit-content;
	}
	.tooltip {
		display: none;
		background-color: #3e3e3e;
		border-radius: 5px;
	}
	.bnav-right button:hover .tooltip {
		display: flex;
	}
	.bnav-right button:hover i {
		color: #fff;
		scale: 1.05;
	}
	.bnav-right button {
		background-color: transparent;
		border: none;
		width: fit-content;
		height: fit-content;
	}

	.bnav-right i {
		transition: 0.1s ease-in-out;
		color: grey;
		font-size: 0.1em;
	}
	#volume-control {
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: row;
		width: 10em;
		height: fit-content;
	}
	/* bottom */
	.bnav {
		display: flex;
		justify-content: space-between;
		align-items: center;
		width: 100%;
		height: 5em;
		background-color: #000;
	}
	.bnav-left {
		display: flex;
		align-items: center;
		width: 35em;
	}
	.playingsong-img {
		width: 3.5em;
		height: 3.5em;
		background-color: red;
		border-radius: 5px;
	}
	.playingsong-info {
		display: flex;
		margin-left: 10px;
		flex-direction: column;
		justify-content: space-evenly;
		align-items: flex-start;
		gap: 3px;
		color: #fff;
	}
	#addtoplaylist {
		display: flex;
		width: 2em;
		height: 2em;
		color: #1ed760;
		justify-content: center;
		align-items: center;
	}
	/* bnav center */
	.bnav-center {
		display: flex;
		flex-direction: column;
		width: 35em;
		height: 75%;
	}
	.songplay-controls {
		display: flex;
		justify-content: center;
		align-items: center;
		gap: 6px;
		width: 100%;
		height: 5em;
	}
	.songplay-timing {
		display: flex;
		justify-content: center;
		align-items: center;
		color: rgb(183, 182, 182);
		font-size: 12px;
		width: 100%;
		height: fit-content;
	}
	/* ------------------ */
	/* sidebar left */
	.left {
		width: fit-content;
	}
	.sidebar-open {
		width: 25em;
	}
	.sidebar-cnt-items > div {
		width: 3.5em;
		height: 3.5em;
		background-color: red;
		border-radius: 5px;
	}
	.sidebar-cnt-items {
		display: flex;
		flex-direction: column;
		width: 100%;
		row-gap: 1em;
	}
	.sidebar-cnt {
		margin-left: 10px;
		margin-top: 15px;
		display: flex;
		flex-direction: column;
		row-gap: 1em;
		grid-column: 1/3;
		height: 30em;
		width: 100%;
		overflow-y: scroll;
		scrollbar-color: grey black;
		scrollbar-width: thin;
		scroll-behavior: smooth;
		justify-content: center;
	}
	.sidebar-icon:hover {
		font-weight: bold;
		color: #fff;
	}
	.sidebar-icon > * {
		height: fit-content;
		font-size: 48px;
		color: rgb(151, 150, 150);
	}
	.sidebar-icon {
		display: flex;
		justify-content: right;
		width: 100%;
		cursor: pointer;
		user-select: none;
		grid-column: 1/3;
		margin-top: 15px;
	}
	.sidebar-left {
		display: grid;
		justify-items: center;
		grid-template-columns: repeat(2, 1fr);
		grid-template-rows: auto 1fr;
		height: 100%;
		background-color: #121212;
		transition: 1s ease-in;
	}
	/* ---------------- */
	.navc {
		justify-content: center;
		grid-area: navc;
	}
	.left {
		justify-content: left;
		grid-area: left;
	}
	.center {
		justify-content: center;
		width: 100%;
		grid-area: center;
	}
	.right {
		justify-content: center;
		width: 100%;
		grid-area: rightI;
	}
	.bnav {
		grid-area: bnav;
		position: absolute;
		bottom: 0;
	}

	.navc,
	.left,
	.center,
	.right,
	.bnav {
		display: flex;
	}
	.home-layout {
		display: grid;
		grid-template-areas:
			'navc navc navc'
			'left center rightI'
			'bnav bnav bnav';
		grid-template-columns: auto 1fr auto;
		grid-template-rows: auto 1fr auto;
		padding: 0.3rem;
		column-gap: 0.5em;
		row-gap: 1em;
		height: 100%;
		min-height: 100vh;
		background-color: #000;
	}
</style>
