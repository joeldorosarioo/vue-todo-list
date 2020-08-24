<template>
	<div class="app-bar">
		<span class="app-bar_left" @click="$emit('left')">
			<i :class="['fa', `fa-${left}`]"></i>
		</span>

		<h1>{{ title }}</h1>

		<span class="app-bar_right" @click="$emit('right')">
			<i :class="['fa', `fa-${right}`]"></i>
		</span>
	</div>
</template>

<script>
	export default {
		props: {
			title: {
				type: String,
				default: ''
			},

			left: {
				type: String,
				default: 'chevron-left'
			},

			right: {
				type: String,
				default: 'ellipsis-v'
			}
		}
	}
</script>

<style lang="scss">
	.app-bar {
		display: flex;
		align-items: center;
		justify-content: space-between;
		height: 55px;

		h1 {
			flex: 1;
			text-align: center;
		}
			
		span {
			padding-right: 20px;
			padding-left: 20px;
		}
	}
</style>
