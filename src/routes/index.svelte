<script>
	import Dropdown from '../components/dropdown/Dropdown.svelte'
	import InputText from '../components/input_text/InputText.svelte'
	import Heading from '../components/heading/Heading.svelte'
	import Checkbox from '../components/checkbox/Checkbox.svelte'

	let cities = [
		{ name: 'London', value: 'london' },
		{ name: 'Paris', value: 'paris' },
		{ name: 'Milan', value: 'milan' }
	]

	let checkboxItems = [
		{ name: 'Item 1', value: 'item1' },
		{ name: 'Item 2', value: 'item2' },
		{ name: 'Item 3', value: 'item3' }
	]

	let selectedCheckboxes = []
	let selectedCity = ''
	let randomName = ''
</script>

<div class="container mx-auto my-8">
	<Heading type="h1" color="000000">Svelte UI</Heading>

	<Heading type="h2" color="000000">Forms</Heading>
	<Heading type="h3" color="000000">Dropdown</Heading>
	<Dropdown label="World Cities" entries={cities} bind:value={selectedCity} />

	<p>Selected value: {selectedCity === '' ? 'none' : selectedCity}</p>

	<Heading type="h3" color="000000">Input Text</Heading>
	<InputText label="A random name" bind:value={randomName} />
	<p>Name : {randomName}</p>

	<Heading type="h3" color="000000">Checkboxes</Heading>

	<Checkbox bind:group={selectedCheckboxes} items={checkboxItems} key="value" />

	{JSON.stringify(selectedCheckboxes)}
</div>
