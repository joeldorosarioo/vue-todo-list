<template>
	<div class="avatar" :class="{ avatar__selected: !!selected }">
		<div class="avatar_face">
			<img src="../assets/avatar.png" />
		</div>

		<h2 class="avatar_name">Hello, Joel.</h2>
		
		<p class="avatar_tips">Looks like feed good.<br />You have {{ todayTasks.length }} tasks to do today.</p>
		<p class="avatar_date">TODAY: {{ today | dateString }}</p>
	</div>
</template>

<script>
	import { mapState, mapGetters } from 'vuex';
	
	export default {
		data () {
			return {
				today: new Date()
			}
		},

		computed: {
			...mapState(['selected']),
			...mapGetters(['todayTasks'])
		},

		filters: {
			dateString (val) {
				return val
				.toDateString()
				.toUpperCase()
				.replace(/(\s\d{4})$/, ', $1')
			}
		}
	}
</script>

<style lang="scss">
	.avatar {
		display: flex;
		flex-direction: column;
		justify-content: flex-end;

		height: 300px;
		padding-left: 40px;
		padding-right: 40px;
		transition: all 0.5s ease;
	}

	.avatar__selected {
		opacity: 0;
		transform: translate3d(0, 20px, 0);
	}
	
	.avatar_face {
		width: 60px;
		height: 60px;
	
		img {
			display: block;
			border-radius: 100%;
			width: 100%;
			height: 100%;
			box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
		}
	}
	
	.avatar_name {
		margin-top: 32px;
		font-size: 2rem;
		letter-spacing: 1px;
		font-weight: 300;
	}

	.avatar_tips {
		margin-top: 16px;
		font-size: 0.875rem;
		font-weight: 100;
		line-height: 1.6em;
		opacity: .9;
	}
		
	.avatar_date {
		margin-top: 40px;
		margin-bottom: 16px;
		font-size: 14px;
	}

	.avatar_name, .avatar_tips, .avatar_date {
		padding-right: 6px;
		padding-left: 6px;
	}
</style>
