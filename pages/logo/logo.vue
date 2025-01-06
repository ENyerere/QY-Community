<template>
	<view class="logo-box">
		<image src="../../logo.png" mode=""></image>
		<text class="text">社区</text>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
	}
</script>

<style>
	.logo-box {
		display: flex;
		flex-direction: column;
		align-items: center;
		position: relative;
		top: 200px;
	}

	image {
		width: 200px;
		height: 200px;
	}

	.text {
		font-size: 20px;
	}
</style>