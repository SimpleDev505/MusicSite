<script lang="ts">
	interface Boptions {
		tooltip?: string;
		tooltip_pos?: string;

		switch_icon_on_click?: boolean;
		switch_icon_name?: string;
		switch_tooltip?: string;

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

		switch_icon_on_click = false,
		switch_icon_name = '',
		switch_tooltip = 'switched',

		has_icon = true,

		icon_name,
		icon_outline = false,
		icon_size = '3em',
		icon_color = '#fff',
		icon_hovercolor = '#fff',
		inv_icon = false,
		b_class = '',

		content = '',
		content_color = '#fff',
		content_size = '16px',

		button_bg = 'transparent',
		button_width = 'fit-content',
		button_height = 'fit-content',
		button_radius = '0',
		button_pad = '0'
	} = $props();

	export function button_click() {}
	let switch_click = $state(false);
</script>

<button
	class={'c-button'}
	style="background-color: {button_bg}; border: none;padding:{button_pad}; width:{button_width}; height:{button_height}; border-radius:{button_radius};"
	onclick={() => {
		button_click;
		switch_click = !switch_click;
		console.log('button click' + switch_click);
	}}
>
	<div
		class="tooltip"
		style="padding: 10px; justify-content: center; align-items: center; width:fit-content; z-index: 10000; height:15px; color: #fff; position: absolute;  transform: {tooltip_pos};"
	>
		{switch_icon_on_click && switch_click ? switch_tooltip : tooltip}
	</div>

	{#if has_icon == true}
		<i
			class={icon_outline ? 'material-symbols-outlined ' + b_class : 'material-icons ' + b_class}
			style="--icon_color:{icon_color}; --icon_hovercolor:{icon_hovercolor}; font-size:{icon_size};{inv_icon
				? 'transform: scaleX(-1);'
				: ''}">{switch_click && switch_icon_on_click ? switch_icon_name : icon_name}</i
		>
	{:else}
		<span style="font-size: {content_size}; color:{content_color}; width:100%; height:100%;"
			>{content}</span
		>
	{/if}
</button>

<style>
	.tooltip {
		display: none;
		background-color: #3e3e3e;
		border-radius: 5px;
	}
	.c-button:hover .tooltip {
		display: flex;
	}
	.c-button i {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}
	.c-button i {
		color: var(--icon_color);
	}
	.c-button:hover i {
		cursor: pointer;
		color: var(--icon_hovercolor);
		scale: 1.15;
	}
</style>
