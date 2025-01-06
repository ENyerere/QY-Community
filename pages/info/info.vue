<template>
	<view class="container">
		<view class="header">
			<text class="xx">消息</text>
			<image src="../../static/业主/search.png" class="search"></image>
			<view class="select-all">
				<view class="select" @click="toggleDropdown">
					<image src="../../static/业主/添加.png" class="select-img"></image>
				</view>
				<transition name="fade">
					<view v-show="isDropdownVisible" class="dropdown">
						<view class="d">发起群聊</view>
						<view class="d">扫一扫</view>
						<view class="d">添加朋友</view>
					</view>
				</transition>
			</view>
		</view>
		<swiper class="swiper" :display-multiple-items="3" previous-margin="50rpx" next-margin="50rpx">
			<swiper-item v-for="(item, index) in list" :key="index" class="swiper-item">
				<view class="swiper-box">
					<image :src="item.src" class="yztx"></image>
					<text>{{ item.name }}</text>
				</view>
			</swiper-item>
		</swiper>
		<uni-list class="info-list">
			<uni-list-chat title="38幢业主总群" :avatar-list="avatarList" note="您收到一条新的消息" time="2020-02-02 20:20"
				badge-positon="left" badge-text="dot" link to="./chat/chat"></uni-list-chat>
			<uni-list-chat title="陈业主" avatar="../../static/业主/yz1.jpg" note="您收到两条新的消息" time="2023-02-11 20:20"
				badge-positon="left" badge-text="2"></uni-list-chat>
			<uni-list-chat title="张业主" avatar="../../static/业主/yz2.jpg" note="您收到一条新的消息" time="2022-02-02 11:30"
				badge-positon="left" badge-text="1"></uni-list-chat>
			<uni-list-chat title="曾业主" avatar="../../static/业主/yz3.jpg" note="曾业主,您门口的法拉利违章停车了,麻烦移..."
				time="2020-04-01 13:20" badge-positon="left" badge-text=""></uni-list-chat>
			<uni-list-chat title="姚业主" avatar="../../static/业主/yz4.jpg" note="姚业主,您订购的送水到家服务,我们已经..."
				time="2020-02-02 20:20" badge-positon="left" badge-text=""></uni-list-chat>
			<uni-list-chat title="邓业主" avatar="../../static/业主/yz5.jpg" note="" time="2020-02-02 20:20"
				badge-positon="left" badge-text=""></uni-list-chat>
			<uni-list-chat title="朱业主" avatar="../../static/业主/yz6.jpg" note="" time="2020-02-02 20:20"
				badge-positon="left" badge-text=""></uni-list-chat>
		</uni-list>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				avatarList: [{
						url: '../../static/业主/yz1.jpg'
					},
					{
						url: '../../static/业主/yz2.jpg'
					},
					{
						url: '../../static/业主/yz3.jpg'
					},
					{
						url: '../../static/业主/yz4.jpg'
					},
					{
						url: '../../static/业主/yz5.jpg'
					},
					{
						url: '../../static/业主/yz6.jpg'
					},
				],
				list: [{
						src: "../../static/业主/yz1.jpg",
						name: "515陈业主"
					},
					{
						src: "../../static/业主/yz2.jpg",
						name: "515张业主"
					},
					{
						src: "../../static/业主/yz3.jpg",
						name: "515曾业主"
					},
					{
						src: "../../static/业主/yz4.jpg",
						name: "515姚业主"
					},
					{
						src: "../../static/业主/yz5.jpg",
						name: "515邓业主"
					},
					{
						src: "../../static/业主/yz6.jpg",
						name: "515朱业主"
					}
				],
				isDropdownVisible: false,
			}
		},
		methods: {
			toggleDropdown() {
				this.isDropdownVisible = !this.isDropdownVisible;
			},
		}
	}
</script>


<style scoped>
	.info-list {
		transform: translate(0px, 10px);
	}

	.container {
		width: 100%;
		padding: 0;
		margin: 0;
		box-sizing: border-box;
	}

	.swiper {
		width: 100%;
		height: 120px;
		transform: translate(0px, 10px);
	}

	.swiper-box {
		width: 80px;
		display: flex;
		flex-direction: column;
		align-items: center;
		text-align: center;
	}

	.swiper-item {
		display: flex;
		flex-direction: column;
		justify-content: center;
		box-sizing: border-box;
	}

	.yztx {
		height: 60px;
		width: 60px;
		border-radius: 50%;
		margin-bottom: 5px;
	}

	.header {
		display: flex;
		flex-direction: row;
		justify-content: flex-end;
	}

	.xx {
		position: absolute;
		left: 200px;
		font-size: 16px;
		font-weight: bold;
	}

	.search {
		height: 24px;
		width: 24px;
		transform: translate(-10px, 0px);
	}

	.select-all {
		position: relative;
	}

	.dropdown {
		position: absolute;
		top: 40px;
		right: 20px;
		background-color: #fff;
		border-radius: 8px;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
		z-index: 10;
		width: 120px;
		transform: translate(10px, -10px);
	}

	.d {
		padding: 10px;
		border-bottom: 1px solid var(--border-color);
	}

	.select-img {
		height: 24px;
		width: 24px;
		margin-left: 10px;
		margin-right: 10px;
	}

	.fade-enter-active,
	.fade-leave-active {
		transition: opacity 0.3s ease-in-out;
	}

	.fade-enter,
	.fade-leave-to {
		opacity: 0;
	}
</style>