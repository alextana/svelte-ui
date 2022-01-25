<script>
	import config from '../../svelte-ui.config.js'

	export let label = ''
	export let value = null
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

<div class="svelte-ui-input__text" style={cssVarStyles}>
	<label for="svelte-ui-input__text" class="block font-bold text-sm mb-1 mt-2">
		{label}
	</label>
	<input
		id="svelte-ui-input__text"
		class="bg-white min-w-80 rounded-lg border-2 border-gray-400 pl-3 pr-8 py-2 {widthClass} {extraClass}
  hover:shadow-lg hover:border-gray-500 transition-all"
		type="text"
		bind:value
	/>
</div>

<style>
	#svelte-ui-input__text {
		background-color: white;
		border-color: var(--primaryGray);
	}
	#svelte-ui-input__text:focus {
		border-color: var(--primaryColor);
	}
</style>
