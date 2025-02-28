<script>
	import Dropcomp from './dropcomp.svelte';
	import Dropdividercomp from './dropdividercomp.svelte';
	import DropItemComp from './dropitemcomp.svelte';
</script>

<Dropcomp
	gap={0}
	contentWidth="195px"
	contentHeight="auto"
	contentBgColor="#282828"
	showIcon={true}
	icon="arrow_drop_down"
	contentTextColor="#fff"
	contentFontWeight="400"
	contentTextGap="10px"
	contentOverallGap="4px"
	contentBorderRadius="6px"
>
	<span slot="trigger">
		<button class="nav-home-button">
			<i class="material-icons">account_circle</i>
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
				<a href="/account" style="color: #fff; text-decoration: none;">Account</a>
				<i class="material-symbols-outlined" style="font-weight: 10;">open_in_new</i>
			</p>
		</DropItemComp>
		<DropItemComp>
			<p
				style="display: flex; width: 100%; align-items: center; justify-content: space-between; margin-left: 8px;"
			>
				<a href="/user" style="color: #fff; text-decoration: none;">Profile</a>
			</p>
		</DropItemComp>
		<DropItemComp>
			<p
				style="display: flex; width: 100%; align-items: center; justify-content: space-between; margin-left: 8px;"
			>
				<a href="/premium" style="color: #fff; text-decoration: none;">Upgrade To Premium</a>
				<i class="material-symbols-outlined" style="font-weight: 10;">open_in_new</i>
			</p>
		</DropItemComp>
		<DropItemComp>
			<p
				style="display: flex; width: 100%; align-items: center; justify-content: space-between; margin-left: 8px;"
			>
				<a href="/support" style="color: #fff; text-decoration: none;">Support</a>
				<i class="material-symbols-outlined" style="font-weight: 10;">open_in_new</i>
			</p>
		</DropItemComp>
		<DropItemComp>
			<p
				style="display: flex; width: 100%; align-items: center; justify-content: space-between; margin-left: 8px;"
			>
				<a href="/download" style="color: #fff; text-decoration: none;">Download</a>
				<i class="material-symbols-outlined" style="font-weight: 10;">open_in_new</i>
			</p>
		</DropItemComp>
		<DropItemComp>
			<p
				style="display: flex; width: 100%; align-items: center; justify-content: space-between; margin-left: 8px;"
			>
				<a href="/settings" style="color: #fff; text-decoration: none;">Settings</a>
			</p>
		</DropItemComp>
		<Dropdividercomp width="100%" height="2px" color="grey" padding="0" />
		<DropItemComp>
			<p
				style="display: flex; width: 100%; align-items: center; justify-content: space-between; margin-left: 8px;"
			>
				<a href="/logout" style="color: #fff; text-decoration: none;">Log Out</a>
			</p>
		</DropItemComp>
	</div>
</Dropcomp>

<style>
	/* profile drop */

	/* profile drop */
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
</style>
