<script lang="ts">
	import TodoTask from '../components/todoTask.svelte';
	import TodoField from '../components/todoField.svelte';
	import type { iTask } from 'src/components/types/iTask';

	let Tasks = [{ id: 0, task: 'Mop the floor before 10AM' }] as iTask[];
</script>

<section
	class="h-screen w-screen flex flex-col justify-start items-center px-16 py-10 gap-y-16 gird-cols-2"
>
	<div
		class="px-6 py-4 text-2xl font-bold alert mx-8 alert-success w-6/10 shadow-lg h-[48px] w-[600px]"
	>
		Welcome to Gus' Svelte Todo App
	</div>
	<TodoField bind:Tasks />
	<div class="flex flex-col justify-start items-center w-full h-full px-48 py-4 gap-y-4">
		{#each Tasks as Task (Task.id)}
			<TodoTask {Task} bind:Tasks />
		{/each}
	</div>
</section>
