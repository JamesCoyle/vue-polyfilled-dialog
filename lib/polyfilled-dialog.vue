<template>
	<dialog v-bind="$attributes" v-on="$listeners"><slot></slot></dialog>
</template>

<script>
export default {
	created() {
		if (typeof window.HTMLDialogElement === 'undefined') {
			import('dialog-polyfill').then((polyfill) => {
				polyfill.registerDialog(this.$el)
			})
		}
	},
}
</script>
