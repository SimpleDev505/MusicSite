<script>
	import Profile from './profile.svelte';
</script>

<div class="nav-cnt">
	<div class="nav-search-cnt">
		<button class="nav-home-button"
			><i class="material-symbols-outlined" style="font-weight: 300;">home</i></button
		>
		<div class="nav-search-grp">
			<div
				style="border-top-left-radius: 500px; border-bottom-left-radius: 500px;"
				class="nav-icon-cnt"
			>
				<span class="material-icons">search</span>
			</div>
			<input id="nav-search" type="text" placeholder="What do you want to listen to?" />
			<div
				style="border-top-right-radius: 500px; border-bottom-right-radius: 500px;"
				class="nav-icon-cnt"
			>
				<span class="material-icons">folder_copy</span>
			</div>
		</div>
		<!-- nav right -->
		<div class="nav-right">
			<button type="button" class="nav-prem">Explore Premium</button>
			<button class="nav-install-app"><i class="material-icons">get_app</i>Install App</button>
			<button class="nav-home-button"><i class="material-icons">notifications</i></button>
			<Profile />
		</div>
	</div>
</div>

<style>
	/* nav right */
	.nav-install-app {
		display: flex;
		background: transparent;
		color: #b3b3b3;
		border: none;
		justify-content: center;
		align-items: center;
		font-weight: 700;
		transition: 0.1s ease-in;
	}
	.nav-install-app:hover {
		transform: scale(1.1);
		color: #fff;
	}
	.nav-prem {
		border-radius: 25px;
		margin: auto;
		color: #000;
		font-weight: 700;
		padding: 0.5em;
		text-align: center;
	}
	.nav-prem:hover {
		transform: scale(1.1);
		background-color: #d8d7d7;
	}
	.nav-right {
		display: flex;
		width: fit-content;
		height: 100%;
		gap:.5em;
	}
	/* nav -- */
	.nav-home-button:hover {
		transition: 0.25s ease-in;
		background: #3e3e3e;
		scale: 1.05;
	}
	.nav-home-button {
		background: #1f1f1f;
		border-radius: 50%;
		width: 48px;
		height: 48px;
		box-shadow: none;
		border: none;
	}
	.nav-home-button i {
		color: #fff;
		margin: 0 auto;
	}
	/* input search */
	.nav-search-cnt {
		display: flex;
		flex: 1;
		justify-content: space-between;
		align-items: center;
	}
	.nav-icon-cnt {
		display: flex;
		width: 4em;
		height: 100%;
		align-items: center;
		background: transparent;
	}
	.nav-search-grp:focus-within {
		transition: 0.22s ease-in;
		border: white solid 3px;
	}
	.nav-search-grp:hover {
		transition: 0.22s ease-in;
		outline: #3e3e3e solid 2px;
	}
	.nav-search-grp:hover {
		background: #2c2c2c;
	}
	.nav-search-grp span {
		color: #fff;
		width: fit-content;
		margin: 0 auto;
	}
	.nav-search-grp {
		display: flex;
		justify-content: center;
		width: 35em;
		height: 100%;
		border-radius: 500px;
		background: #1f1f1f;
	}
	.nav-search-grp input {
		width: 100%;
		height: 100%;
		background: transparent;
		box-shadow: none;
		border: none;
		outline: none;
		color: #fff;
		font-weight: 700;
	}
	/* other */
	.nav-cnt {
		display: flex;
		width: 100%;
		height: 3em;
	}
</style>
