<template>
	<dialog v-bind="$attributes" v-on="$listeners"><slot></slot></dialog>
</template>

<script>
import DialogPolyfill from 'dialog-polyfill'

export default {
	mounted() {
		if (typeof window.HTMLDialogElement === 'undefined') {
			DialogPolyfill.registerDialog(this.$el)
		}
	},
}
</script>
