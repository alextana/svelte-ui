<script>
	export let id = ''
	export let extraClass = ''
</script>

<label for={id} class="block font-bold text-sm mb-1 mt-2 {extraClass}"><slot /></label>
