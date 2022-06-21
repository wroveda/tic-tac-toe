<template>
	<header>
		<h1>TIC TAC TOE</h1>
	</header>
	<TurnIndicator :turnMark="turn"/>
	<div class="cont-slot">
		<MarkSlot :turnMark="turn"/>
		<MarkSlot :turnMark="turn"/>
		<MarkSlot :turnMark="turn"/>
		<MarkSlot :turnMark="turn"/>
		<MarkSlot :turnMark="turn"/>
		<MarkSlot :turnMark="turn"/>
		<MarkSlot :turnMark="turn"/>
		<MarkSlot :turnMark="turn"/>
		<MarkSlot :turnMark="turn"/>
	</div>
	<button id="btn-reset">Reset</button>
</template>


<script>
import MarkSlot from "./components/MarkSlot.vue";
import TurnIndicator from "./components/TurnIndicator.vue";

export default {
	name: "App",
	components: {
		MarkSlot,
		TurnIndicator
	},
	data() {
		return {
			turn: "x"
		}
	}
}
</script>


<style>
@font-face {
	font-family: "Iosevka Aile";
	src: "./assets/font/iosevka-aile-regular.ttf"
}

* {
	font: "Iosevka Aile";
	--clr-fg: #fecea8;
	--clr-bg: #2a363b;
	--clr-acc: #99b898;
	--clr-acc-x: #4e92b5;
	--clr-acc-o: #b54e4e;
	--clr-faded: #5d6468;
}

body {
	background: var(--clr-bg);
}

h1 {
	color: var(--clr-bg);
	background-color: var(--clr-acc);
	padding: 0 1em;
	margin-top: 0;
	margin-bottom: 0.5em;
}

button {
	font-size: 1rem;
	color: var(--clr-bg);
	background-color: var(--clr-acc);
	cursor: pointer;
	width: fit-content;
	padding: 0.5em;
	border: 0;
	border-radius: 0.2em;
	margin: 0.2em;
}

#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	color: var(--clr-fg);
	display: flex;
	flex-direction: column;
	align-items: center;
	width: fit-content;
	border-radius: 0.2em;
	margin: 0 auto;
	margin-top: 60px;
	box-shadow: 0 0 30px rgba(0, 0, 0, 0.2);
}

.cont-slot {
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	grid-template-rows: repeat(3, 1fr);
	width: fit-content;
	margin-bottom: 0.5em;
}

#btn-reset {
	font-weight: 700;
	padding: 0.5em 3em;
	margin-bottom: 1em;
}
</style>
