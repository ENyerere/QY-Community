<template>
	<view class="container">
		<image class="product-image" src="../../../static/swiperImg/轮播图2.png" mode="widthFix"></image>
		<text class="product-description" space="ensp">
			
		</text>
	</view>
</template>

<script>
	export default {
		data() {
			return {
                image:[]
			};
		}
	};
</script>

<style>
	.container {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		padding: 20rpx;
	}

	.product-image {
		width: 100%;
		margin-top: 20rpx;
	}

	.product-description {
		font-size: 35rpx;
		color: #666;
		margin-top: 25rpx;
		text-align: left;
		text-indent: 70rpx;
	}
</style>
