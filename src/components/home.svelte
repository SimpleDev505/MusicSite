<script lang="ts">
	import Buttonwithtooltip from './buttonwithtooltip.svelte';
	import Navbar from './navbar.svelte';
	import Progresscomp from './progresscomp.svelte';
	import Scrolllistchild from './scrolllistchild.svelte';
	import Centerplaylist from './centerplaylist.svelte';
	import Sidebarplaylistcomp from './sidebarplaylistcomp.svelte';
	import Rightsongview from './rightsongview.svelte';
	let sidebaropen = $state(false);
	let controls_over = $state(false);
	let scroll_center = $state(false);
	let sidebar_search = $state(false);
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

	// temp credits
	const credits = [
		{ author: 'Aniruth', role: 'Composer' },
		{ author: 'ARR', role: 'Lyricist' }
	];
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
				{#if sidebaropen == true}
					<span style="font-size: 1.25em; font-weight: 600;">Your Library</span>
				{/if}
			</button>
			<div class="sidebar-cnt">
				<div class="sidebar-cnt-items">
					{#if sidebaropen == true}
						<div class="sidebar-filter-bts">
							<Buttonwithtooltip
								icon_name=""
								has_icon={false}
								button_bg="#2A2A2A"
								content="Playlists"
								tooltip="filter"
								button_radius="15px"
								button_pad="8px 12px"
								content_size="14px"
							></Buttonwithtooltip>
							<Buttonwithtooltip
								icon_name=""
								has_icon={false}
								button_bg="#2A2A2A"
								content="Artists"
								tooltip="filter"
								button_radius="15px"
								button_pad="8px 12px"
								content_size="14px"
							></Buttonwithtooltip>
							<Buttonwithtooltip
								icon_name=""
								has_icon={false}
								button_bg="#2A2A2A"
								tooltip="filter"
								content="Albums"
								button_radius="15px"
								button_pad="8px 12px"
								content_size="14px"
							></Buttonwithtooltip>
						</div>
						<div class="sidebar-search">
							<div class="sidebar-search-btn">
								<Buttonwithtooltip
									button_bg="transparent"
									button_pad="5px"
									button_radius="50px"
									tooltip="Search In Your Library"
									icon_name="search"
									icon_size="23px"
									icon_hovercolor="white"
									icon_color="grey"
									switch_tooltip=""
								></Buttonwithtooltip>
							</div>
							<input class={sidebar_search ? 'sidebar-input-open' : ''} />
						</div>
					{/if}
					<Scrolllistchild
						onscrolllist={() => {}}
						onscrolllistReturn={() => {}}
						items_Rowgap="1em"
						height="30em"
						width="100%"
						scroll_visible={false}
					>
						<Sidebarplaylistcomp sidebaropen_value={sidebaropen}></Sidebarplaylistcomp>
						<Sidebarplaylistcomp sidebaropen_value={sidebaropen}></Sidebarplaylistcomp>
						<Sidebarplaylistcomp sidebaropen_value={sidebaropen}></Sidebarplaylistcomp>
						<Sidebarplaylistcomp sidebaropen_value={sidebaropen}></Sidebarplaylistcomp>
						<Sidebarplaylistcomp sidebaropen_value={sidebaropen}></Sidebarplaylistcomp>
						<Sidebarplaylistcomp sidebaropen_value={sidebaropen}></Sidebarplaylistcomp>
						<Sidebarplaylistcomp sidebaropen_value={sidebaropen}></Sidebarplaylistcomp>
						<Sidebarplaylistcomp sidebaropen_value={sidebaropen}></Sidebarplaylistcomp>
						<Sidebarplaylistcomp sidebaropen_value={sidebaropen}></Sidebarplaylistcomp>
						<Sidebarplaylistcomp sidebaropen_value={sidebaropen}></Sidebarplaylistcomp>
						<Sidebarplaylistcomp sidebaropen_value={sidebaropen}></Sidebarplaylistcomp>
						<Sidebarplaylistcomp sidebaropen_value={sidebaropen}></Sidebarplaylistcomp>
						<Sidebarplaylistcomp sidebaropen_value={sidebaropen}></Sidebarplaylistcomp>
						<Sidebarplaylistcomp sidebaropen_value={sidebaropen}></Sidebarplaylistcomp>
					</Scrolllistchild>
				</div>
			</div>
		</div>
	</div>
	<div class="center">
		<!-- <Centerhome></Centerhome> -->
		<Centerplaylist></Centerplaylist>
	</div>
	<div class="right">
		<Rightsongview {credits}></Rightsongview>
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
				<Buttonwithtooltip
					switch_icon_name="volume_off"
					switch_icon_on_click={true}
					switch_tooltip="Mute"
					icon_color="grey"
					tooltip_pos="translate(-15px,-25px)"
					icon_name="volume_down"
					tooltip="Volume"
					icon_outline={false}
					icon_size="1.5em"
				></Buttonwithtooltip>

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
		overflow: visible;
	}
	.songplay-timing {
		display: flex;
		justify-content: center;
		align-items: center;
		color: rgb(183, 182, 182);
		font-size: 12px;
		width: 100%;
		height: fit-content;
		column-gap: 10px;
	}
	/* ------------------ */
	/* sidebar left */
	.left {
		width: fit-content;
	}
	.sidebar-open {
		width: 25em;
	}
	.sidebar-filter-bts {
		display: flex;
		flex-direction: row;
		width: 100%;
		height: fit-content;
		justify-content: flex-start;
		column-gap: 10px;
		align-items: center;
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
		scrollbar-color: transparent transparent;
		justify-content: space-between;
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
		justify-content: flex-start;
		align-items: center;
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
	.sidebar-search {
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center;
		width: 100%;
		height: fit-content;
		margin-top: 10px;
	}
	.sidebar-search-btn {
		margin-top: 5px;
		margin-bottom: 5px;
		position: absolute;
		z-index: 2;
	}
	.sidebar-search input {
		outline: #3e3e3e solid 1px;
		border: none;
		background: #1f1f1f;
		margin: 0;
		position: fixed;
		z-index: 1;
		height: 25px;
		width: 0;
		display: none;
		border-radius: 2px;
		transition: 0.2s ease-in-out;
	}
	.sidebar-input-open {
		display: block;
		width: 3em;
	}
	/* ---------------- */
	.navc {
		justify-content: center;
		grid-area: navc;
		overflow: hidden;
	}
	.left {
		justify-content: left;
		grid-area: left;
		width: fit-content;
		overflow: hidden;
	}
	.center {
		display: flex;
		justify-content: center;
		grid-area: center;
		height: 100%;
		/* width: clamp(30em, 100%, 75%); */
		overflow: hidden;
		width: 100%;
	}
	.right {
		grid-area: rightI;
		width: 100%;
		/* width: clamp(5em, 100%, 25em); */
		overflow: hidden;
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
		grid-template-columns: auto auto auto;
		grid-template-rows: auto 1fr auto;
		padding: 0.3rem;
		height: 100%;
		min-height: 100vh;
		background-color: #000;
	}
</style>
