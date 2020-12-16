<template>
	<h1>Reaction Timer Game</h1>

	<button class="control" @click="startGame" :disabled="isPlaying">
		<span>Start game!</span>
		<span>🔥</span>
	</button>

	<Block v-if="isPlaying" :delay="delay" @gameEnded="handleGameEnded" />
</template>

<script>
import Block from "./components/Block";

export default {
	name: "App",
	components: {
		Block,
	},
	data() {
		return {
			isPlaying: false,
			delay: null,
			showResults: false
		};
	},
	methods: {
		startGame() {
			this.delay = 2000 + Math.random() * 5000;
			this.isPlaying = true;
		},
		handleGameEnded(results) {

		}
	},
};
</script>

<style>
.control {
	border: 1px solid rgb(67, 21, 192);
	outline: 0;
	background: transparent;
	font-size: 16px;
	padding: 10px 20px;
	border-radius: 5px;
	display: flex;
	justify-content: space-between;
	align-items: center;
	margin: 0 auto 2em;
	cursor: pointer;
}
.control span:last-child {
	margin-left: 10px;
}
.control:disabled {
	border-color: lightgray;
	cursor: not-allowed;
}
</style>
