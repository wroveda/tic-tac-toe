<template>
	<button :style="{'background-color': bgColor}">
		<fa-icon v-show="mark === 0" icon="fa-solid fa-x" />
		<fa-icon v-show="mark === 1" icon="fa-regular fa-circle" />
	</button>
</template>

<script>
function turnNum() {
	this.mark = this.turnNum % 2;
	switch (this.mark) {
		case 0: 
			this.bgColor = "var(--clr-acc-x)";
			break;
		case 1: 
			this.bgColor = "var(--clr-acc-o)";
			break;
		default: 
			this.bgColor = "var(--clr-faded)";
	}
}

export default {
	name: "MarkSlot",
	props: {
		turnNum: Number,
	},
	watch: {
		turnNum,
	},
	data() {
		return {
			mark: -1,
			bgColor: "var(--clr-faded)"
		}
	}
}
</script>

<style scoped>
button {
	font-size: 2rem;
	width: 3rem;
	height: 3rem;
	padding: 0;
}
</style>
