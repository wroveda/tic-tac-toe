<template>
	<header>
		<h1>TIC TAC TOE</h1>
	</header>
	<TurnIndicator v-show="!isEnded" :turnNum="turn"/>
	<WinIndicator v-show="isEnded" :turnNum="turn" :isTie="isTie"/>
	<div class="cont-slot">
		<MarkSlot @click="onMarkSlotClick(0)" :turnNum="board[0]"/>
		<MarkSlot @click="onMarkSlotClick(1)" :turnNum="board[1]"/>
		<MarkSlot @click="onMarkSlotClick(2)" :turnNum="board[2]"/>
		<MarkSlot @click="onMarkSlotClick(3)" :turnNum="board[3]"/>
		<MarkSlot @click="onMarkSlotClick(4)" :turnNum="board[4]"/>
		<MarkSlot @click="onMarkSlotClick(5)" :turnNum="board[5]"/>
		<MarkSlot @click="onMarkSlotClick(6)" :turnNum="board[6]"/>
		<MarkSlot @click="onMarkSlotClick(7)" :turnNum="board[7]"/>
		<MarkSlot @click="onMarkSlotClick(8)" :turnNum="board[8]"/>
	</div>
	<button id="btn-reset" @click="resetBoard">Reset</button>
</template>


<script>
import MarkSlot from "./components/MarkSlot.vue";
import TurnIndicator from "./components/TurnIndicator.vue";
import WinIndicator from "./components/WinIndicator.vue";

function resetBoard() {
	this.board = [-1, -1, -1, -1, -1, -1, -1, -1, -1];
	this.turn = 0;
	this.isEnded = false;
	this.isTie = false;
}

function onMarkSlotClick(id) {
	if (this.board[id] != '-1' || this.isEnded) { return }
	
	let mark = this.turn % 2;
	this.board[id] = mark;
	
	// Win check for rows and columns
	for (let i = 0; i < 3; i++) {
		if (this.board[0 + i*3] === mark
			&& this.board[1 + i*3] === mark
			&& this.board[2 + i*3] === mark
			||
			this.board[0 + i] === mark
			&& this.board[3 + i] === mark
			&& this.board[6 + i] === mark) {
				this.isEnded = true;
		// Win check for diagonals
		} else if (this.board[0] === mark
			&& this.board[4] === mark
			&& this.board[8] === mark
			||
			this.board[2] === mark
			&& this.board[4] === mark
			&& this.board[6] === mark
			) {
				this.isEnded = true;
		}
	}
	console.log(this.turn);
	console.log(mark);
	// Tie check
	if ( this.turn >= 8 ) {
		this.isEnded = true;
		this.isTie = true;
	} else if (!this.isEnded){
		this.turn += 1;
	}
	
}

export default {
	name: "App",
	components: {
		MarkSlot,
		TurnIndicator,
		WinIndicator
	},
	methods: {
		resetBoard,
		onMarkSlotClick
	},
	data() {
		return {
			turn: 0,
			board: [-1, -1, -1, -1, -1, -1, -1, -1, -1],
			isEnded: false,
			isTie: false
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
