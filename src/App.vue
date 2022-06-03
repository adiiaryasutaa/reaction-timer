<template>
	<main class="flex flex-col items-center w-full p-10">
		<header class="mb-10">
			<h1 class="text-3xl font-medium text-slate-800 border-b-4 border-green-600">Reaction Timer</h1>
		</header>
		<button @click="start" class="bg-emerald-600 rounded text-slate-50 font-medium px-6 py-2 hover:bg-emerald-700 active:bg-emerald-800 disabled:bg-emerald-500 disabled:text-slate-200" :disabled="isPlaying">Start</button>
		<Block v-if="isPlaying" :delay="delay" @end="endGame" />
		<Result v-if="showResult" :score="score" />
	</main>
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
	name: 'App',
	data() {
		return {
			isPlaying: false,
			delay: null,
			score: null,
			showResult: false
		}
	},
	methods: {
		start() {
			this.delay = 2000 + Math.random() * 5000
			this.isPlaying = true
			this.showResult = false
		},
		endGame(reactionTime) {
			this.score = reactionTime
			this.isPlaying = false
			this.showResult = true
		}
	},
	components: {
    Block,
    Result
}
}
</script>

