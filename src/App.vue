<template>
	<header>
		<h1>TIC-TAC-TOE</h1>
	</header>
	<TurnIndicator v-show="!isEnded" :turnNum="turn"/>
	<WinIndicator v-show="isEnded" :turnNum="turn" :isTie="isTie"/>
	<div class="cont-slot">
		<!-- Slots are 0 indexed -->
		<MarkSlot v-for="slotID in 9" :key="slotID - 1" @click="onMarkSlotClick(slotID - 1)" :turnNum="board[slotID - 1]"/>
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
	// Check if the game has ended or the slot has already been filled.
	if ( this.isEnded || this.board[id] != '-1') { return }
	
	// Converts the turn into the corresponding mark.
	// x = 0 | o = 1
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
		}
	}
	// Win check for diagonals
	if (this.board[0] === mark
		&& this.board[4] === mark
		&& this.board[8] === mark
		||
		this.board[2] === mark
		&& this.board[4] === mark
		&& this.board[6] === mark
		) {
			this.isEnded = true;
	}
	// Tie check
	else if ( this.turn >= 8 ) {
		this.isEnded = true;
		this.isTie = true;
	}
	// Continue to next turn
	else if (!this.isEnded){
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
	font-family: "Iosevka Aile Lite";
	src: "./assets/font/iosevka-aile-lite-regular.ttf"
}

* {
	--clr-fg: #fecea8;
	--clr-bg: #2a363b;
	--clr-acc: #99b898;
	--clr-acc-x: #4e92b5;
	--clr-acc-o: #b54e4e;
	--clr-faded: #5d6468;
	font-family: "Iosevka Aile Lite", sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
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

.cont-ind {
	font-size: 1.5rem;
	display: flex;
	align-items: center;
	margin-bottom: 0.5em;
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
