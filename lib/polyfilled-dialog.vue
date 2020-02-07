<template>
	<dialog v-bind="$attributes" v-on="$listeners"><slot></slot></dialog>
</template>

<script>
export default {
	methods: {
		get open() {
			return this.$el.open
		},

		showModal() {
			this.$el.showModal()
		},

		show() {
			this.$el.show()
		},

		close() {
			this.$el.close()
		},
	},

	created() {
		if (typeof window.HTMLDialogElement === 'undefined') {
			import('dialog-polyfill').then((polyfill) => {
				polyfill.default.registerDialog(this.$el)
			})
		}
	},
}
</script>
