
<template lang='pug'>

	li(
		:class='{ completed: todoDataItem.completed }'
		@click.self='toggle(todoDataItem.id)'
	)
		| {{ todoDataItem.title }}
		button(
			class='icon delete'
			@click='_delete(todoDataItem.id)'
		)

</template>


<script>
	export default {
		name: 'TodoItem',
		props: [ 'todoDataItem' ],
		methods: {
			toggle(id) { this.$store.dispatch('toggleTodo', id) },
			_delete(id) { this.$store.dispatch('deleteTodo', id) }
		}
	}
</script>


<style lang='stylus' scoped>

	@import '../styles/variables.styl'
	@import '../styles/animation.styl'
	@import '../styles/icon.styl'

	li
		position relative
		padding 0 10px
		margin-bottom 15px
		height 40px
		line-height 40px
		background: linear-gradient(to right, #FFF 50%, $color-green 50%)
		background-size 200% 100%
		background-position left bottom
		color #111
		transition all .2s
		overflow hidden
		// transition-name background, box-shadow
		// transition-duration .2s
		// opacity 0
		// animation move-from-left .4s, fade-in .2s .2s
		// animation-fill-mode forwards
		// animation-timing-function linear
		cursor pointer
		user-select none
		&:hover
			box-shadow 5px 5px 0px #111
			.icon
				&.delete
					opacity 1

		&.completed
			background-position right bottom


		.icon
			&.delete
				position absolute
				top 0
				right 0
				bottom 0
				margin auto
				opacity 0
				// z-index 99

</style>