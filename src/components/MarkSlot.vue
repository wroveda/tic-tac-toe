<template>
	<button @click="switchState" :style="{'background-color': bgColor}">
		<fa-icon v-show="mark === 'x'" icon="fa-solid fa-x" />
		<fa-icon v-show="mark === 'o'" icon="fa-regular fa-circle" />
	</button>
</template>

<script>
function switchState() {
	this.mark = this.turnMark;
	switch (this.mark) {
		case "x": 
			this.bgColor = "var(--clr-acc-x)";
			break;
		case "o": 
			this.bgColor = "var(--clr-acc-o)";
			break;
		default: 
			this.bgColor = "var(--clr-faded)";
	}
}

export default {
	name: "MarkSlot",
	props: {
		turnMark: String
	},
	methods: {
		switchState
	},
	data() {
		return {
			mark: "None",
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
