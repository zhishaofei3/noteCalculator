<style scoped lang="sass">
	.result {
		color: #FFAE54;
	}
</style>
<template>
	<div class="result">
		收入和：<span>{{receipt}}</span>
		<br>
		支出和：<span>{{expenditure}}</span>
		<br>
		总和：<span>{{sum}}</span>
	</div>
</template>
<script>
	export default {
		props: ['sum', 'receipt', 'expenditure']
	}
</script>