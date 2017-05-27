<style scoped lang="sass">
	.h1 {
		margin-bottom: 30px;
	}
	.index {
		width: 100%;
		position: absolute;
		top: 0;
		bottom: 0;
		left: 0;
		text-align: center;
	.txt {
		width: 300px;
		margin: 0 auto;
	}
	}
</style>
<template>
	<div class="index">
		<Row type="flex" justify="center" align="middle">
			<Col span="24">
			<h1 class="h1">记事本价格计算器</h1>
			<compute-textarea @updateChange="reCount"></compute-textarea>
			<compute-result :sum="sum" :receipt="receipt" :expenditure="expenditure"></compute-result>
			</Col>
		</Row>
	</div>
</template>
<script type="text/ecmascript-6">
	import computeTextarea from './compute-textarea.vue'
	import computeResult from './compute-result.vue'
	export default {
		data() {
			return {
				receipt: 0,
				expenditure: 0,
				sum: 0
			}
		},
		methods: {
			tipHandler (tipContent) {
				this.$Modal.info({
					title: '提示',
					content: tipContent
				});
			},
			reCount(arr) {
				this.sum = this.formatFloat(arr.reduce((pre, cur) => pre + cur))

				this.receipt = 0
				arr.forEach((cur) => {
					if (cur > 0) {
						this.receipt += cur
						console.log(this.receipt);
					}
				})

				this.receipt = this.formatFloat(this.receipt)

				this.expenditure = 0
				arr.forEach((cur) => {
					if (cur < 0) {
						this.expenditure += Math.abs(cur)
					}
				})
				this.expenditure = this.formatFloat(this.expenditure)
			},
			formatFloat(f, digit=2) {
				var m = Math.pow(10, digit)
				return Math.round(f * m) / m
			}
		},
		components: {
			computeTextarea,
			computeResult
		}
	}
</script>
