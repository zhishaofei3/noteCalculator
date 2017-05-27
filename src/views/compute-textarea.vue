<style type="text/css" scoped lang="sass">
	.input-wrap {
		width: 300px;
		margin: 0 auto 10px;
	}
</style>
<template>
	<div class="input-wrap">
		<Input type="textarea" :rows="10" v-model="str"/>
	</div>
</template>
<script type="text/ecmascript-6">
	export default {
		data () {
			return {
				str: ''
			}
		},
		watch: {
			str (newStr) {
				var moneyArr = newStr.match(/[+-]*\d+(\.(\d+))*/g)
				var arr = [0]
				if (moneyArr && moneyArr.length) {
					arr = moneyArr.map((numStr) => Number.parseFloat(numStr))
				}
				this.$emit('updateChange', arr)
			}
		}
	}
</script>
