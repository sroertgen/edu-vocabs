<script>
	import { db, handleFilterSelect } from '$lib/db';
	import CaretDown from '$lib/icons/CaretDown.svelte';

	let { title, filterKey } = $props();
</script>

<div class="dropdown">
	<div
		tabindex="0"
		role="button"
		class="mt-2
    w-52
    select-none
    rounded-lg
    border
    border-gray-300
    bg-white
    px-2
    py-2
    text-gray-700
    shadow-sm
    focus:outline-none
    focus:ring-2
    focus:ring-gray-300"
	>
		<div class="flex flex-row items-center justify-between">
			<span>{title}</span>
			<CaretDown />
		</div>
		<ul
			class="menu dropdown-content z-[1] mt-3 max-h-96 w-64 flex-nowrap overflow-y-auto rounded-box bg-base-100 p-2 shadow"
		>
			{#each $db.filters[filterKey] as filterVal}
				<li
					class="overflow-hidden rounded"
					class:bg-info={$db.selectedFilters[filterKey].includes(filterVal)}
					class:text-black={$db.selectedFilters[filterKey].includes(filterVal)}
				>
					<button
						type="button"
						role="option"
						aria-selected={$db.selectedFilters[filterKey].includes(filterVal)}
						onclick={() => handleFilterSelect(filterKey, filterVal)}
					>
						{filterVal}
					</button>
				</li>
			{/each}
		</ul>
	</div>
</div>
