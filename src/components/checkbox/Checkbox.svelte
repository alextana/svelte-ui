<script>
	import { fly } from 'svelte/transition'
	import config from '../../svelte-ui.config.js'
	import Label from '../label/Label.svelte'

	export let items = []
	export let group
	export let key = ''
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

{#if items.length}
	{#each items as item}
		{@const id = `svelte-ui-checkbox-${Math.floor(Math.random() * 100000)}`}
		<div class="svelte-ui-checkbox__item flex gap-3 mb-2 items-center" style={cssVarStyles}>
			<Label {id}>{item.name}</Label>
			<div class="svelte-ui-checkbox__container w-8 h-8 overflow-hidden relative">
				<input
					class="{extraClass} border-2 overflow-hidden rounded-md appearance-none w-8 h-8 p-3 {item.checked
						? 'svelte-ui-checkbox__checked'
						: 'svelte-ui-checkbox__unchecked'}"
					style={item.checked
						? 'border-color: var(--primaryColor);'
						: 'border-color: var(--primaryGray);'}
					{id}
					type="checkbox"
					bind:checked={item.checked}
					bind:group
					value={item[key]}
				/>
				{#if item.checked}
					<svg
						transition:fly|local={{ duration: 300, y: 100, delay: 150 }}
						xmlns="http://www.w3.org/2000/svg"
						class="pointer-events-none absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 w-8 h-8"
						viewBox="0 0 20 20"
						fill="white"
					>
						<path
							fill-rule="evenodd"
							d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
							clip-rule="evenodd"
						/>
					</svg>
				{/if}
			</div>
		</div>
	{/each}
{:else}
	<p>no items</p>
{/if}

<style>
	.svelte-ui-checkbox__item input {
		position: relative;
	}
	.svelte-ui-checkbox__item input::after {
		transition: 0.35s var(--easing);
		width: 0px;
		position: absolute;
		left: 50%;
		top: 50%;
		transform: translate(-50%, -50%);
		height: 0px;
		content: '';
		display: block;
	}
	.svelte-ui-checkbox__item input.svelte-ui-checkbox__checked::after {
		width: 100%;
		position: absolute;
		border-radius: 50%;
		left: 50%;
		top: 50%;
		transform: translate(-50%, -50%) scale(1.5);
		height: 100%;
		content: '';
		display: block;
		background-color: var(--primaryColor);
	}
</style>
