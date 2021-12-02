<template>
	<view class="">
		第一次
		<u-button text="默认按钮" size="normal" type="info" ></u-button>
		<u--text text="我用十年青春,赴你最后之约"></u--text>
		<u--text type="primary" text="主色"></u--text>
		<u--text type="error"   text="错误"></u--text>
		<u--text type="success" text="成功"></u--text>
		<u--text type="warning" text="警告"></u--text>
		<u--text type="info"    text="信息"></u--text>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style lang="scss" scoped>
	@import "@/uni_modules/uview-ui/libs/css/components.scss";
</style>
