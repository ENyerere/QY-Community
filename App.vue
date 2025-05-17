<script>
	export default {
		onLaunch: function() {
			uni.navigateTo({
				url: '/pages/logo/logo'
			});

			setTimeout(() => {
				uni.reLaunch({
					url: '/pages/my/my'
				});
			}, 2000);
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
</style>