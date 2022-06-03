<template>
	<div class="flex flex-col items-center space-y-4 p-10">
		<p class="text-slate-800 font-medium">Reaction time: <span class="font-bold text-emerald-600">{{ score }}</span> ms</p>
		<p :class="{ 'text-red-600': score <= 250, 'text-green-600': score <= 400, 'text-slate-600': score > 400 }" class="text-4xl font-extrabold">{{ rank }}</p>
	</div>
</template>

<script>
export default {
	props: ['score'],
	data() {
		return {
			rank: null
		}
	},
	mounted() {
		if (this.score <= 250) {
			this.rank = 'NINJAAAAAA'
		} else if (this.score <= 400) {
			this.rank = 'Wow Rapid Reflexes'
		} else {
			this.rank = 'Snail pace :D'
		}
	}
}
</script>