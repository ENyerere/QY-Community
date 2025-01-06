<template>
	<view>
		<view class="tupian">
			<image class="背景图" src="../../../static/person/背景.jpg"></image>
		</view>
		<view class="info">
			<image class="userinfo-avatar" :src="avatarUrl" @click="changeAvatar"></image>
			<h2 style="transform: translate(5%, -50%);">{{nickname}}</h2>
			<view class="status-container">
				<view class="status-item">
					<text class="status-number">{{ likes }}</text>
					<text class="status-label">获赞</text>
				</view>
				<view class="status-item">
					<text class="status-number">{{ followed }}</text>
					<text class="status-label">被关注</text>
				</view>
				<view class="status-item">
					<text class="status-number">{{ following }}</text>
					<text class="status-label">关注</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				avatarUrl: '../../../static/person/头像5.JPG',
				nickname: '小易热心市民',
				likes: 0,
				followed: 0,
				following: 16
			}
		},
		methods: {
			changeAvatar() {
				uni.chooseImage({
					count: 1,
					success: (res) => {
						this.avatarUrl = res.tempFilePaths[0];
					},
					fail: (err) => {
						uni.showToast({
							title: '图片选择失败',
							icon: 'none'
						});
					}
				});
			},
		}
	}
</script>

<style>
	.tupian {
		height: 241.875px;
		width: 430px;
	}

	.背景图 {
		height: 241.875px;
		width: 430px;
		transform: translate(0%, -5%);
	}

	.info {
		transform: translate(0%, -25%);
		background-color: white;
		height: 225px;
		width: 430px;
		border-radius: 16px;
	}

	.userinfo-avatar {
		height: 96px;
		width: 96px;
		left: 15%;
		transform: translate(-50%, -25%);
		border-radius: 50%;
		border: 3px solid #ffffff;
	}

	.status-container {
		display: flex;
		justify-content: space-around;
		padding: 0px;
		background-color: #ffffff;
		transform: translate(165px, -160%);
		height: 80px;
		width: 225px;
		align-items: center;
	}

	.status-item {
		text-align: center;
	}

	.status-number {
		font-size: 24px;
		font-weight: bold;
		color: #333;
	}

	.status-label {
		font-size: 14px;
		color: #666;
	}

	/* 	.number {
		background-color: darkgrey;
		transform: translate(175px, -160%);
		height: 80px;
		width: 224px;
	} */
</style>