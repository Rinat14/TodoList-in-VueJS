<template>
	<div class="w-96 mx-auto">
		<h1 class="text-4xl font-bold text-center mt-10">TodoList</h1>
		<form class="flex mb-8">
			<input type="text" v-model="newTask" class="px-4 py-2 border outline-none w-full mt-4" placeholder="Add the task..">
			<button
				class="bg-sky-400 px-4 py-2 mt-4"
				@click.prevent="addTask()"
				>Add
			</button>
		</form>
		<ul class="">
			<li :key="task" v-for="(task, index) in tasks" class="flex justify-between items-center border mb-4">
				<button
					@click="completedTask(task)"
					:class="task.completed ? 'bg-green-600 line-through text-white' : ''"
					class="px-4 py-2 w-full flex justify-start">
					{{ index + 1 + '.' }} {{ task.title }}
				</button>
				<button @click="removeTask(index)" class="px-4 py-2 bg-rose-500 text-white">Remove</button>
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
		name: 'App',
		components: {},
		data(){
			return {
				newTask: '',
				tasks: [
					{
						title: 'Practise with Tailwind',
						completed: false
					}
				]
			}
		},
		methods: {
			addTask() {
				this.tasks.push({
					title: this.newTask,
					completed: false
				});
				this.newTask = '';
			},
			completedTask(task) {
				task.completed = !task.completed;
			},
			removeTask(index) {
				this.tasks.splice(index, 1);
			}
		}
	}
</script>

<style>
</style>
