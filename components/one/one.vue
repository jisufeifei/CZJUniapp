<template>
	<view>
		这是组件
	</view>
</template>

<script>
	export default {
		name:"one",
		data() {
			return {
				
			};
		},
		beforeCreate() {
			console.log('beforeCreate')
		},
		created() {
			console.log('created')
		},
		mounted(){
			console.log('mounted')
		},
		destroyed() {
			console.log('destroyed')
		}
	}
</script>

<style>

</style>
