<template>
	<button @click="this.mark = this.turnMark">
		<fa-icon v-show="mark === 'x'" icon="fa-solid fa-x" size="xl" />
		<fa-icon v-show="mark === 'o'" icon="fa-regular fa-circle" size="xl" />
	</button>
</template>

<script>
export default {
	name: "MarkSlot",
	props: {
		turnMark: String
	},
	data() {
		return {
			mark: "None"
		}
	}
}
</script>

<style scoped>
button {
	background-color: var(--clr-faded);
	width: 3em;
	height: 3em;
	padding: 0;
}
</style>
