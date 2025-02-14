<script lang="ts">
	interface Boptions {
		tooltip?: string;
		tooltip_pos?: string;
		icon_name: string;
		icon_outline?: boolean;
		icon_size?: string;
		icon_color?: string;
		icon_hovercolor?: String;
		inv_icon?: boolean;
		b_class?: string;
	}

	let {
		tooltip = 'Play',
		tooltip_pos = 'translate(-10px,-25px)',
		icon_name,
		icon_outline = false,
		icon_size = '3em',
		icon_color = '#fff',
		icon_hovercolor = '#fff',
		inv_icon = false,
		b_class = ''
	} = $props();
</script>

<button class={'c-button'} style="background-color: transparent; border: none;padding:0;">
	<div
		class="tooltip"
		style="padding: 10px; justify-content: center; align-items: center; width:fit-content; z-index: 1000; height:15px; color: #fff; position: absolute;  transform: {tooltip_pos};"
	>
		{tooltip}
	</div>
	<i
		class={icon_outline ? 'material-symbols-outlined ' + b_class : 'material-icons ' + b_class}
		style="--icon_color:{icon_color}; --icon_hovercolor:{icon_hovercolor}; font-size:{icon_size};{inv_icon
			? 'transform: scaleX(-1);'
			: ''}">{icon_name}</i
	>
</button>

<style>
	.tooltip {
		display: none;
		background-color: #3e3e3e;
		border-radius: 5px;}
	.c-button:hover .tooltip {
		display: flex;
	}
	.c-button i {
		color: var(--icon_color);
	}
	.c-button:hover i {
		color: var(--icon_hovercolor);
		scale: 1.05;
	}
</style>
