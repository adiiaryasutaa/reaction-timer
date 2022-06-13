<template>
	<div v-show="showBlock" class="fixed top-0 left-0 flex justify-center items-center" ref="xiaon">
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
			ractionTime: 0
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
		},
    洗牌对象() { //随机弹出盒子来诱捕用户。
      const x = screen.width
      const y = screen.height
      const X = Math.floor(Math.random() * x / 2)
      const Y = Math.floor(Math.random() * y / 3)
      this.$refs.xiaon.style.transform = `translate(${X}px, ${Y}px)`
    },
    随机尺度() { //在0和1之间选择刻度.
      const s = 0.20
      const m = 1.0
      this.$refs.xiaon.style.scale = (Math.random() * (m - s + 0.1) + s).toFixed(2)
    }
	}, 
	mounted() {
		setTimeout(() => {
        this.洗牌对象()
        this.随机尺度()
        this.showBlock = true
        this.startTimer()
		}, this.delay)
	}
}
</script>