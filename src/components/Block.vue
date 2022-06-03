<template>
	<div v-if="showBlock" class="fixed top-0 left-0 flex justify-center items-center h-screen w-screen bg-slate-900/50">
		<div @click="stopTimer" class="flex items-center justify-center w-[400px] h-[200px] bg-blue-600 rounded text-slate-50 font-medium cursor-pointer hover:bg-blue-700 active:bg-blue-800">
			Click
		</div>
	</div>
</template>

<script>
export default {
	props: ['delay'],
	data() {
		return {
			showBlock: false,
			timer: null,
			ractionTime: 0,
		}
	},
	methods: {
		startTimer() {
			this.timer = setInterval(() => {
				this.ractionTime += 10
			}, 10)
		},
		stopTimer() {
			clearInterval(this.timer)
			this.$emit('end', this.ractionTime)
		}
	}, 
	mounted() {
		setTimeout(() => {
			this.showBlock = true
			this.startTimer()
		}, this.delay)
	}
}
</script>