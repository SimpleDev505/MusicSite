<script lang="ts">
	// The progress value (0 to 100)
	export let progress: number = 0;

	// Height of the progress bar (any valid CSS height value)
	export let height: string = '20px';

	// Background color of the progress bar track
	export let backgroundColor: string = '#e0e0e0';

	// Color of the progress fill (the bar that fills as progress increases)
	export let fillColor: string = '#3b82f6';

	// Border radius of the progress bar
	export let borderRadius: string = '10px';
	export let width: string = '100%';
</script>

<!-- The outer container represents the track.
     Inline styles use the exported props for customization. -->
<div
	class="progress-bar"
	style="height: {height}; width:{width}; background-color: {backgroundColor}; border-radius: {borderRadius};"
>
	<!-- The inner container represents the fill. Its width is set by the progress percentage. -->
	<div class="progress-fill" style="width: {progress}%; background-color: {fillColor};"></div>
</div>

<style>
	.progress-bar {
		margin-left: 15px;
		margin-right: 15px;
		overflow: hidden;
	}
	.progress-fill {
		height: 100%;
		transition: width 0.3s ease;
	}
</style>
