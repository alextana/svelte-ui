<script>
	import config from '../../svelte-ui.config.js'

	export let value = ''
	export let label = ''
	export let entries = []
	export let widthClass = ''
	export let extraClass = ''

	let styles = {
		primaryColor: config.appearance.colors.primaryColor,
		secondaryColor: config.appearance.colors.secondaryColor,
		primaryGray: config.appearance.colors.primaryGray,
		easing: config.animations.transition.easing
	}

	$: cssVarStyles = Object.entries(styles)
		.map(([key, value]) => `--${key}:${value}`)
		.join(';')
</script>

<div class="svelte-ui-dropdown relative" style={cssVarStyles}>
	<label for="svelte-ui-dropdown__select" class="block font-bold text-sm mb-1 mt-2">
		{label}
	</label>
	<select
		id="svelte-ui-dropdown__select"
		class="
      appearance-none min-w-80 rounded-lg border-2 pl-3 pr-8 py-2 {widthClass} {extraClass}
      hover:shadow-lg transition-all
    "
		bind:value
	>
		<option value="">Please select...</option>
		{#each entries as entry}
			<option value={entry.value}>
				{entry.name}
			</option>
		{/each}
	</select>
</div>

<style>
	select {
		-webkit-appearance: none;
		-moz-appearance: none;
		background: transparent;
		background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='20' height='20' viewBox='0 0 20 20' fill='gray'><path fill-rule='evenodd' d='M10 3a1 1 0 01.707.293l3 3a1 1 0 01-1.414 1.414L10 5.414 7.707 7.707a1 1 0 01-1.414-1.414l3-3A1 1 0 0110 3zm-3.707 9.293a1 1 0 011.414 0L10 14.586l2.293-2.293a1 1 0 011.414 1.414l-3 3a1 1 0 01-1.414 0l-3-3a1 1 0 010-1.414z' clip-rule='evenodd'/></svg>");
		background-repeat: no-repeat;
		background-position-x: 98%;
		background-position-y: 50%;
	}

	select:hover {
		background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='20' height='20' viewBox='0 0 20 20' fill='black'><path fill-rule='evenodd' d='M10 3a1 1 0 01.707.293l3 3a1 1 0 01-1.414 1.414L10 5.414 7.707 7.707a1 1 0 01-1.414-1.414l3-3A1 1 0 0110 3zm-3.707 9.293a1 1 0 011.414 0L10 14.586l2.293-2.293a1 1 0 011.414 1.414l-3 3a1 1 0 01-1.414 0l-3-3a1 1 0 010-1.414z' clip-rule='evenodd'/></svg>");
	}

	#svelte-ui-dropdown__select {
		background-color: white;
		border-color: var(--primaryGray);
	}

	#svelte-ui-dropdown__select:hover {
		border-color: var(--primaryColor);
	}
</style>
