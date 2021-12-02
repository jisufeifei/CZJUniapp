<script>
	export default {
		//应用的生命周期
		
		//应用初始化完成执行，全局只执行一次
		onLaunch: function() {
			console.log('App Launch')
		},
		//应用显示的时候执行，或者从后台进入前台
		onShow: function() {
			console.log('App Show')
		},
		//应用隐藏的时候执行，或者从前台进入后台
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>


<style lang="scss">
	@import "./uni_modules/uview-ui/theme.scss";
	/*每个页面公共css */
</style>
