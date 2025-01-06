<template>
	<view class="head">
		<view>
			<swiper class="swiper" circular=true autoplay="true" duration="1000" interval="2000" indicator-dots="true"
				indicator-color="white" indicator-active-color="black">
				<swiper-item v-for="(item,index) in swiperImgUrl">
					<navigator :url="item.detail">
						<image class="swiper-img" :src="item.img"></image>
					</navigator>
				</swiper-item>
			</swiper>
			<uni-section class="list1">
				<view v-for="(item, index) in glist1" class="v-item" :key="index">
					<navigator :url="item.detail">
						<view class="v-item-box">
							<text class="text">{{ item.text }}</text>
						</view>
					</navigator>
				</view>
			</uni-section>
			<uni-section class="list2">
				<view v-for="(item, index) in glist2" class="v-item" :key="index">
					<navigator :url="item.detail">
						<view class="v-item-box">
							<text class="text">{{ item.text }}</text>
						</view>
					</navigator>
				</view>
			</uni-section>

		</view>


	</view>
</template>

<script>
	export default {
		data() {
			return {
				swiperImgUrl: [{
					img: "../../static/swiperImg/轮播图1.png",
					detail: "/pages/store/carpuselDetail/carpuselDetail1",
				}, {
					img: "../../static/swiperImg/轮播图2.png",
					detail: "/pages/store/carpuselDetail/carpuselDetail2",
				}],
				glist1: [{
					text: "物业缴费",
					detail: "/pages/store/c/c1",
				}, {
					text: "管道维修",
					detail: "/pages/store/c/c2",
				}, {
					text: "开锁换锁",
					detail: "/pages/store/c/c3",
				}, {
					text: "家电维修",
					detail: "/pages/store/c/c4",
				}],
				glist2: [{
					text: "水电维修",
					detail: "/pages/store/c/c5",
				}, {
					text: "家政保洁",
					detail: "/pages/store/c/c6",

				}, {
					text: "防水补漏",
					detail: "/pages/store/c/c7",

				}, {
					text: "送水到家",
					detail: "/pages/store/c/c8",

				}],
				showRight: false
			}
		},


		methods: {
			onPullDownRefresh() {
				setTimeout(() => {
					this.scollViewImg = this.scollViewImg.sort(() => Math.random() - 0.5);
					this.swiperlist = this.swiperlist.map(v => {
						return v.sort(() => Math.random() - 0.5)
					});
				}, 2000);
				uni.stopPullDownRefresh();
			},
		}
	};
</script>

<style lang="scss">
	@import "@/uni_modules/uview-ui/index.scss";

	.head {
		overflow-y: scroll;
		overflow-x: hidden;
		background-size: cover;
		background-repeat: no-repeat;
		box-sizing: border-box;
		background-image: url("../../static/background.jpg");
	}

	.swiper {
		height: 146px;
		width: 350px;
		margin: 0 auto;
		margin-top: 10px;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
		backdrop-filter: blur(10px);
	}

	.swiper-img {
		height: 146px;
		width: 350px;
	}

	.scroll-item {
		height: 214px;
		width: 179px;
		display: inline-block;
	}

	.scroll-bottom {
		height: 20px;
		width: 50px;
		border: 1px solid black;
		font-size: 8px;
		text-align: center;
	}

	.scroll-bottom-view {
		display: flex;
		justify-content: space-around;
	}

	.tabs {
		display: flex;
		justify-content: space-evenly;
	}

	.grid-img {
		height: 100%;
		width: 100%;
	}

	.swiper-grid {
		height: 200px;
		margin: 0 auto;
	}

	.uni-icon-right {
		height: 18px;
		width: 18px;
	}

	.scroll_horizontal {
		border: 1px solid #f3f3f3;
		height: 300rpx;
		margin: 0 auto;
		white-space: nowrap;
	}

	.scroll_vertical {
		border: 1px solid #f3f3f3;
		height: 600rpx;
		margin: 0 auto;
	}

	.scroll-flex {
		display: flex;
	}

	.uni-grid-flex {
		display: flex;
	}

	.v-item-box {
		height: 125px;
		width: 160px;
		display: flex;
		flex-direction: column;
		align-items: center;
		border-radius: 20px;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
		background-color: rgba(255, 255, 255, 0.3);
		/* 半透明背景 */
		backdrop-filter: blur(5px);
		/* 虚化效果 */
	}

	.list1 {
		display: flex;
		flex-wrap: wrap;
		gap: 10px;
		transform: translate(1%, 10%);
		background-color: rgba(255, 255, 255, 0);
		/* 半透明背景 */
	}

	.list2 {
		display: flex;
		flex-wrap: wrap;
		gap: 10px;
		transform: translate(49%, -90%);
		background-color: rgba(255, 255, 255, 0);
	}

	.v-item {
		margin: 10px 0 10px 0;
		flex: 1 1 calc(50% - 20px);
		min-width: 150px;
	}

	.text {
		position: relative;
		top: 40px;
		font-size: 30px;
	}
</style>