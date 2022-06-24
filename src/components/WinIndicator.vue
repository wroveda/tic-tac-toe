<template>
	<div>
		<div class="win-indicator" v-show="!isTie">
			<div class="mark-x"><fa-icon v-show="turnNum % 2 === 0" icon="fa-solid fa-x" /></div>
			<div class="mark-o"><fa-icon v-show="turnNum % 2 === 1" icon="fa-regular fa-circle" /></div>
			<div class="text">WINS</div>
		</div>
		<div class="win-indicator" v-show="isTie">
			<div class="text">TIE</div>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		turnNum: Number,
		isTie: Boolean
	}
}
</script>

<style scoped>
.win-indicator {
	font-size: 1.5rem;
	display: flex;
	align-items: center;
	margin-bottom: 0.5em;
}

.mark-x {
	font-size: 2rem;
	margin-right: 0.5em;
	color: var(--clr-acc-x);
}

.mark-o {
	font-size: 2rem;
	margin-right: 0.5em;
	color: var(--clr-acc-o);
}
</style>
