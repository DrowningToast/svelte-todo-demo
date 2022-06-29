<script lang="ts">
	import { fade } from 'svelte/transition';
	import type { iTask } from './types/iTask';
	export let Task: undefined | iTask;
	export let Tasks: iTask[];
	export let checked = false;
	let timeoutId: NodeJS.Timeout | undefined;

	$: if (checked && !timeoutId) {
		timeoutId = setTimeout(() => {
			Tasks = [
				...Tasks.filter((task) => {
					return task.id !== Task?.id;
				})
			];
		}, 5000);
	}
	$: if (!checked) {
		clearTimeout(timeoutId);
		timeoutId = undefined;
	}
</script>

<div
	transition:fade
	on:click={() => (checked = true)}
	class={`text-center content-center text-xl h-16 grid place-items-center ${
		checked ? 'bg-gray-500 line-through' : 'bg-blue-600 hover:scale-105'
	}  w-full text-white font-semibold rounded-lg  duration-500 relative cursor-pointer`}
>
	<h1 class={`duration-200 ${checked ? 'opacity-50' : 'opacity-100'}`}>{Task?.task}</h1>
	<input
		bind:checked
		type="checkbox"
		class="absolute toggle left-12 top-1/2 transform -translate-y-1/2"
	/>
</div>
