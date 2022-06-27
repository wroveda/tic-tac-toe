<template>
	<div>
		<div class="cont-ind" v-show="!isTie">
			<div class="mark-x"><fa-icon v-show="turnNum % 2 === 0" icon="fa-solid fa-x" /></div>
			<div class="mark-o"><fa-icon v-show="turnNum % 2 === 1" icon="fa-regular fa-circle" /></div>
			<div>WINS</div>
		</div>
		<div class="cont-ind" v-show="isTie">
			<div class="tie">TIE</div>
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
/* Maintains the alignment with the win indicator */
.tie {
	margin: 0.25em 0;
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
