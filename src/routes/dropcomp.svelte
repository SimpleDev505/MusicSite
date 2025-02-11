<script lang="ts">
	import { onMount, tick } from 'svelte';

	// --- Customization Parameters for the Dropdown Content ---
	export let gap: number = 4; // Gap (in pixels) between the trigger and the content
	export let contentWidth: string = 'auto'; // "auto" will match the trigger's width
	export let contentHeight: string = 'auto'; // "auto" for natural height
	export let contentBgColor: string = '#fff'; // Background color of the dropdown content
	export let contentTextColor: string = '#000'; // Text color inside the dropdown content
	export let contentBorderRadius: string = '0.25rem'; // Border radius for the dropdown content
	export let contentFontWeight: string = 'normal'; // Font weight for the dropdown content
	// This parameter controls the spacing between elements inside the content.
	export let contentTextGap: string = '0.5rem';
	export let contentOverallGap: string = '0.5rem';

	// --- Customization Parameters for the Trigger Icon ---
	export let showIcon: boolean = false;
	export let icon: string = 'expand_more'; // Material icon name (ensure Material Icons font is loaded)

	// --- Parameter for Click Events on Dropdown Items ---
	// This callback is invoked when the dropdown content receives a click or keyboard activation.
	export let onItemClick: (e: MouseEvent) => void = () => {};

	// --- Internal State and Element References ---
	let isOpen: boolean = false;
	let triggerEl: HTMLElement;
	let dropdownContentEl: HTMLElement;

	// Holds the computed position for the dropdown content.
	let dropdownPosition: { top: number; left: number; width: number } = {
		top: 0,
		left: 0,
		width: 0
	};

	/**
	 * Toggle the dropdown's open/closed state.
	 * When opening, wait for the DOM to update before calculating the position.
	 */
	async function toggleDropdown(): Promise<void> {
		isOpen = !isOpen;
		if (isOpen) {
			await tick();
			updateDropdownPosition();
		}
	}

	/**
	 * Calculate and update the dropdown content's position so that it appears
	 * over all elements and stays within the viewport.
	 */
	function updateDropdownPosition(): void {
		if (!triggerEl || !dropdownContentEl) return;

		const triggerRect = triggerEl.getBoundingClientRect();
		let top = triggerRect.bottom + gap;
		let left = triggerRect.left;
		const width = triggerRect.width;

		const contentRect = dropdownContentEl.getBoundingClientRect();
		const viewportWidth = window.innerWidth;
		const viewportHeight = window.innerHeight;

		// Adjust horizontally if the dropdown would overflow on the right.
		if (left + contentRect.width > viewportWidth) {
			left = Math.max(10, viewportWidth - contentRect.width - 10);
		}

		// Adjust vertically if the dropdown would overflow at the bottom.
		if (top + contentRect.height > viewportHeight) {
			const newTop = triggerRect.top - contentRect.height - gap;
			if (newTop >= 0) {
				top = newTop;
			}
		}

		dropdownPosition = { top, left, width };
	}

	/**
	 * Custom Svelte action: Closes the dropdown if a click occurs outside the node.
	 */
	function clickOutside(node: HTMLElement) {
		const handleClick = (event: MouseEvent) => {
			const target = event.target as Node;
			if (node && !node.contains(target) && triggerEl && !triggerEl.contains(target)) {
				isOpen = false;
			}
		};

		document.addEventListener('click', handleClick, true);
		return {
			destroy() {
				document.removeEventListener('click', handleClick, true);
			}
		};
	}

	/**
	 * Handler for clicks within the dropdown content.
	 * It invokes the user-supplied onItemClick callback.
	 */
	function handleContentClick(e: MouseEvent) {
		onItemClick(e);
	}

	/**
	 * Handler for keyboard events on the dropdown content.
	 * If the user presses Enter or Space, trigger onItemClick.
	 */
	function handleContentKeydown(e: KeyboardEvent) {
		if (e.key === 'Enter' || e.key === ' ') {
			e.preventDefault();
			const syntheticEvent = new MouseEvent('click', { bubbles: true });
			onItemClick(syntheticEvent);
		}
	}

	/**
	 * Recalculate the dropdown position when the window is resized or scrolled.
	 */
	function handleWindowChange() {
		if (isOpen) {
			updateDropdownPosition();
		}
	}

	// Register window event listeners after the component mounts.
	onMount(() => {
		window.addEventListener('resize', handleWindowChange);
		window.addEventListener('scroll', handleWindowChange, true);

		return () => {
			window.removeEventListener('resize', handleWindowChange);
			window.removeEventListener('scroll', handleWindowChange, true);
		};
	});
</script>

<!-- Trigger Container -->
<div class="dropdown">
	<div
		class="dropdown-trigger"
		bind:this={triggerEl}
		role="button"
		tabindex="0"
		on:click={toggleDropdown}
		on:keydown={(e) => {
			if (e.key === 'Enter' || e.key === ' ') {
				e.preventDefault();
				toggleDropdown();
			}
		}}
	>
		<slot name="trigger">
			<!-- Default trigger button (includes an icon if showIcon is true) -->
			<button type="button">
				Toggle Dropdown
				{#if showIcon}
					<span class="material-icons">{icon}</span>
				{/if}
			</button>
		</slot>
	</div>
</div>

<!-- Dropdown Content -->
{#if isOpen}
	<div
		class="dropdown-content"
		bind:this={dropdownContentEl}
		use:clickOutside
		role="menu"
		tabindex="0"
		on:click={handleContentClick}
		on:keydown={handleContentKeydown}
		style="
      top: {dropdownPosition.top}px;
      left: {dropdownPosition.left}px;
      width: {contentWidth === 'auto' ? dropdownPosition.width + 'px' : contentWidth};
      height: {contentHeight};
      background-color: {contentBgColor};
      color: {contentTextColor};
      border-radius: {contentBorderRadius};
      font-weight: {contentFontWeight};
      display: flex;
      flex-direction: column;
      gap: {contentTextGap};
      padding:{contentOverallGap};
    "
	>
		<slot name="content">
			<!-- Default dropdown content -->
			<p>Dropdown Content</p>
		</slot>
	</div>
{/if}

<style>
	.dropdown {
		display: inline-block;
	}
	.dropdown-trigger {
		cursor: pointer;
		display: inline-block;
	}
	.dropdown-content * {
		transition: 0.2s ease;
	}

	.dropdown-content {
		text-align: left;
		position: fixed;
		border: none;
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
		z-index: 10000; /* Overlays all other elements */
	}
	/* Optional Material Icons styling (ensure the Material Icons font is loaded) */
	.material-icons {
		vertical-align: middle;
		margin-left: 0.25rem;
	}
</style>
