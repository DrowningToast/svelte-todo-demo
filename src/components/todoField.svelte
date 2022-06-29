<script lang="ts">
	import type { iTask } from './types/iTask';

	export let Tasks = [] as iTask[];
	let currentTask = '';
	let incremental = 1;

	export let addTask: (e: MouseEvent) => void = (e) => {
		e.preventDefault();
		if (!currentTask) return alert('Please enter your task first');
		Tasks = [...Tasks, { id: incremental++, task: currentTask }];
		currentTask = '';
	};
</script>

<div>
	<div class="form-control">
		<label class="label" for="task">
			<span class="label-text">Describe your task here</span>
		</label>
		<div class="flex justify-around items-center gap-x-8">
			<label class="input-group">
				<span>Task</span>
				<input
					bind:value={currentTask}
					type="text"
					id="task"
					placeholder="Wash dishes"
					class="input input-bordered w-80"
				/>
			</label>
			<button class="btn btn-primary" on:click={addTask}> Add </button>
		</div>
	</div>
</div>
