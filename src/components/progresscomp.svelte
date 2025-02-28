<script lang="ts">
	let {
		progress = 0, // Progress value (0 to 100)
		height = '20px', // Height
		width = '100%', // Width
		backgroundColor = '#e0e0e0', // Track color
		fillColor = '#3b82f6', // Fill color
		borderRadius = '10px',
		onProgress = (value: number) => {}
	} = $props();

	let isDragging = false;
	let progressBar: HTMLDivElement;

	function updateProgress(clientX: number) {
		if (!progressBar) return;
		const rect = progressBar.getBoundingClientRect();
		let newProgress = Math.min(100, Math.max(0, ((clientX - rect.left) / rect.width) * 100));
		progress = newProgress;
		onProgress(progress);
	}

	function startDrag(event: MouseEvent | TouchEvent) {
		isDragging = true;
		updateProgress(event instanceof MouseEvent ? event.clientX : event.touches[0].clientX);
	}

	function stopDrag() {
		isDragging = false;
	}

	function handleDrag(event: MouseEvent | TouchEvent) {
		if (isDragging) {
			updateProgress(event instanceof MouseEvent ? event.clientX : event.touches[0].clientX);
		}
	}

	function handleKeydown(event: KeyboardEvent) {
		if (event.key === 'ArrowLeft') {
			progress = Math.max(0, progress - 5);
		} else if (event.key === 'ArrowRight') {
			progress = Math.min(100, progress + 5);
		}
		onProgress(progress);
	}
</script>

<!-- Progress Bar Container -->
<div
	bind:this={progressBar}
	class="progress-bar"
	style="width:{width}; height:{height}; background-color:{backgroundColor}; border-radius:{borderRadius};"
	role="slider"
	aria-valuenow={progress}
	aria-valuemin="0"
	aria-valuemax="100"
	aria-label="Progress slider"
	tabindex="0"
	onmousedown={startDrag}
	onmouseup={stopDrag}
	onmousemove={handleDrag}
	onmouseleave={stopDrag}
	ontouchstart={startDrag}
	ontouchend={stopDrag}
	ontouchmove={handleDrag}
	onkeydown={handleKeydown}
>
	<!-- Progress Fill -->
	<div class="progress-fill" style="width: {progress}%; --fillcolor: {fillColor};">
		<span class="material-icons"> circle </span>
	</div>
</div>

<style>
	.progress-bar {
		position: relative;
		cursor: pointer;
		user-select: none;
		display: flex;
		align-items: center;
		outline: none;
	}

	.progress-fill {
		position: relative;
		display: flex;
		justify-content: flex-end;
		align-items: center;
		height: 100%;
		transition: 0.2s ease-in-out;
		background-color: var(--fillcolor);
	}
	.progress-fill span {
		display: none;
		width: 10px;
		position: absolute;
		z-index: 100000;
		color: white;
		font-size: 16px;
	}
	.progress-bar:hover {
		opacity: 0.9;
	}
	.progress-bar:hover .progress-fill {
		background-color: rgb(52, 247, 52);
	}
	.progress-bar:hover .progress-fill span {
		display: inline-block;
	}
</style>
