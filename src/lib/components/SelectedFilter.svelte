<script>
	import { handleFilterSelect } from '$lib/db';
	let { val, key } = $props();
</script>

<button
	aria-label="Filter {val} entfernen"
	onclick={() => handleFilterSelect(key, val)}
	class="badge badge-info select-none gap-2"
>
	<svg
		xmlns="http://www.w3.org/2000/svg"
		fill="none"
		viewBox="0 0 24 24"
		class="inline-block h-4 w-4 stroke-current"
	>
		<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"
		></path>
	</svg>
	{val}
</button>
