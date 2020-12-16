<template>
	<div class="block" v-if="showBlock" @click="stopTimer">
		<p>Click here</p>
	</div>
</template>

<script>
export default {
	name: "Block",
	props: ["delay"],

	data() {
		return {
			showBlock: false,
			timer: null,
			reactionTime: 0,
		};
	},

	mounted() {
		setTimeout(() => {
			this.showBlock = true;
			this.startTimer();
		}, this.delay);
	},

	methods: {
		startTimer() {
			this.timer = setInterval(() => {
				this.reactionTime += 10;
			}, 10);
		},

		stopTimer() {
			clearInterval(this.timer);
			this.$emit('gameEnded', { reactionTime })
		},
	},
};
</script>

<style>
.block {
	width: 300px;
	height: 300px;
	margin: 0 auto;
	background: rgb(67, 21, 192);
	color: #fff;
	border-radius: 15px;
	display: flex;
	justify-content: center;
	align-items: center;
	cursor: pointer;
}

h1 {
	text-align: center;
}
</style>
