<script>
	export let type = ''
	export let extraClass = ''
	export let color = ''

	function setColor() {
		return color.charAt(0) === '#' ? color : '#' + color
	}
</script>

{#if type === 'h1'}
	<h1 class="text-4xl font-extrabold {extraClass}" style="color: {setColor()}"><slot /></h1>
{:else if type === 'h2'}
	<h2 class="text-3xl font-extrabold {extraClass}" style="color: {setColor()}"><slot /></h2>
{:else if type === 'h3'}
	<h3 class="text-2xl font-extrabold {extraClass}" style="color: {setColor()}"><slot /></h3>
{:else if type === 'h4'}
	<h4 class="text-xl font-extrabold {extraClass}" style="color: {setColor()}"><slot /></h4>
{:else if type === 'h5'}
	<h5 class="text-md font-extrabold {extraClass}" style="color: {setColor()}"><slot /></h5>
{/if}
