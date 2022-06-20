<template>
	<button>
		<fa-icon v-show="false" icon="fa-regular fa-circle" size="xl" />
		<fa-icon v-show="false" icon="fa-solid fa-x" size="xl" />
	</button>
</template>

<script>
export default {
	name: "MarkSlot"
}
</script>

<style lang="scss" scoped>
button {
	background-color: var(--clr-faded);
	width: 3em;
	height: 3em;
	padding: 0;
}
</style>
