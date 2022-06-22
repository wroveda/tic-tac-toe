<template>
	<div class="turn-ind">
		<div class="mark-x" :class="{active: turnMark === 'x'}"><fa-icon icon="fa-solid fa-x" /></div>
		<div class="turn-ind__text">TURN</div>
		<div class="mark-o" :class="{active: turnMark === 'o'}"><fa-icon icon="fa-regular fa-circle" /></div>
	</div>
</template>

<script>
export default {
	name: "TurnIndicator",
	props: {
		turnMark: String
	},
}
</script>

<style scoped>
.turn-ind {
	font-size: 1.5rem;
	display: flex;
	align-items: center;
	margin-bottom: 0.5em;
}

.turn-ind__text {
	margin: 0 1em;
}

.mark-x,
.mark-o {
	font-size: 2rem;
	color: var(--clr-faded);
}

.mark-x.active {
	color: var(--clr-acc-x);
}

.mark-o.active {
	color: var(--clr-acc-o);
}
</style>
