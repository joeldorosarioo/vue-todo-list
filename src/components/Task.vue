<template>
	<transition name="fade">
		<div class="task" v-if="!task.deleted">
			<input :id="id" type="checkbox" v-model="task.done" />
			<label :for="id">{{ task.title }}</label>
			
			<transition name="fade">
				<span class="task_delete" v-show="task.done" @click="deleteTask({ task })">
					<i class="fa fa-trash"></i>
				</span>
			</transition>
		</div>
	</transition>
</template>

<script>
	import { mapMutations } from 'vuex';
	let GID = 1;

	export default {
		props: {
			task: {
				type: Object,
				required: true
			}
		},
	
		data () {
			return {
				id: `task-${GID++}`
			}
		},
	
		methods: {
			...mapMutations(['deleteTask'])
		}
	}
</script>

<style lang="scss">
	.task {
		display: flex;
		padding-top: 12px;
		padding-bottom: 12px;
		font-size: 14px;
		border-bottom: 1px solid #EEEEEE;
	}

	.task input {
		display: none;
	}
		
	.task label {
		flex: 1;
		line-height: 20px;
	}

	.task label:before, .task label:after {
		content: '';
		display: inline-block;
		margin-right: 20px;
		margin-top: 1px;
		width: 14px;
		height: 14px;
		vertical-align: top;
	}

	.task label:before {
		border: 1px solid #ccc;
		border-radius: 2px;
		background-color: white;
	}

	.task label:after {
		position: relative;
		content: '\f00c';
		display: none;
		margin-right: -16px;
		z-index: 10;
		width: 10px;
		height: 10px;
		padding: 3px;
		border-radius: 2px;
		font: normal normal normal 10px/1 FontAwesome;
		color: white;
		background-color: #CCCCCC;
		float: left;
	}

	.task input:checked + label:after {
		display: inline-block;
	}

	.task_delete {
		padding: 0 10px;
		color: #CCCCCC;
		font-size: 16px;
	}

	.fade-leave-to, .fade-enter {
		opacity: 0;
	}

	.fade-enter-to, .fade-leave {
		opacity: 1;
	}

	.fade-enter-active,
	.fade-leave-active {
		transition: all 0.3s ease;
	}
</style>
