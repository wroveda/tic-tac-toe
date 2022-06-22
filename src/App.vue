<template>
	<header>
		<h1>TIC TAC TOE</h1>
	</header>
	<TurnIndicator :turnMark="turn"/>
	<div class="cont-slot">
		<MarkSlot @click="onMarkSlotClick(0)" :mark="board[0]"/>
		<MarkSlot @click="onMarkSlotClick(1)" :mark="board[1]"/>
		<MarkSlot @click="onMarkSlotClick(2)" :mark="board[2]"/>
		<MarkSlot @click="onMarkSlotClick(3)" :mark="board[3]"/>
		<MarkSlot @click="onMarkSlotClick(4)" :mark="board[4]"/>
		<MarkSlot @click="onMarkSlotClick(5)" :mark="board[5]"/>
		<MarkSlot @click="onMarkSlotClick(6)" :mark="board[6]"/>
		<MarkSlot @click="onMarkSlotClick(7)" :mark="board[7]"/>
		<MarkSlot @click="onMarkSlotClick(8)" :mark="board[8]"/>
	</div>
	<button id="btn-reset" @click="resetBoard">Reset</button>
</template>


<script>
import MarkSlot from "./components/MarkSlot.vue";
import TurnIndicator from "./components/TurnIndicator.vue";

function resetBoard() {
	this.board = ['', '', '', '', '', '', '', '', ''];
	this.turn = 'x';
}

function onMarkSlotClick(id) {
	if (this.board[id] != "") { return }
	
	this.board[id] = this.turn;
	
	// Win check for rows and columns
	for (let i = 0; i < 3; i++) {
		if (this.board[0 + i*3] === this.turn
			&& this.board[1 + i*3] === this.turn
			&& this.board[2 + i*3] === this.turn
			||
			this.board[0 + i] === this.turn
			&& this.board[3 + i] === this.turn
			&& this.board[6 + i] === this.turn) {
				console.log("Win");
			}
	}
	// Win check for diagonals
	if (this.board[0] === this.turn
		&& this.board[4] === this.turn
		&& this.board[8] === this.turn
		||
		this.board[2] === this.turn
		&& this.board[4] === this.turn
		&& this.board[6] === this.turn
		) {
			console.log("Win");
	}
	
	this.turn = this.turn === 'x' ? 'o' : 'x';
}

export default {
	name: "App",
	components: {
		MarkSlot,
		TurnIndicator
	},
	methods: {
		resetBoard,
		onMarkSlotClick
	},
	data() {
		return {
			turn: 'x',
			board: ['', '', '', '', '', '', '', '', '']
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
