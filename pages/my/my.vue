<template>
	<view>
		<!--个人区域-->
		<div>
			<view class="userinfo">
				<image class="userinfo-avatar" :src="avatarUrl" @click="changeAvatar"></image>
				<h2 style="position: absolute; left: 20%; top: 15px;" @click="person">{{nickname}}</h2>
				<text style="position: absolute; left: 20%; top: 45px; font-size: 12px; color: #888888;"
					@click="person">点击查看个人主页</text>
			</view>
			<view class="auth-button">
				<text class="auth-text">成蹊苑38幢</text>
			</view>
		</div>
		<!--my页面列表-->
		<view>
			<view class="my-info">
				<view class="my-info-item">
					<text class="my-info-item-num">{{ likes }}</text>
					<text class="my-info-item-label">获赞</text>
				</view>
				<view style="font-size: 10px; color: #bebebe;">|</view>
				<view class="my-info-item">
					<text class="my-info-item-num">{{ followed }}</text>
					<text class="my-info-item-label">被关注</text>
				</view>
				<view style="font-size: 10px; color: #bebebe;">|</view>
				<view class="my-info-item">
					<text class="my-info-item-num">{{ following }}</text>
					<text class="my-info-item-label">关注</text>
				</view>
				<view style="font-size: 10px; color: #bebebe;">|</view>
				<view class="my-info-item">
					<text class="my-info-item-num">{{ good }}</text>
					<text class="my-info-item-label">最近点赞</text>
				</view>
			</view>

			<view class="small-tools">
				<image src="../../static/my/tools/咨询服务.png" class="small-tools-img-1"></image>
				<image src="../../static/my/tools/业务流程.png" class="small-tools-img-2"></image>
				<image src="../../static/my/tools/服务大厅.png" class="small-tools-img-3"></image>
				<image src="../../static/my/tools/校园热点.png" class="small-tools-img-4"></image>
				<image src="../../static/my/tools/校园风景.png" class="small-tools-img-5"></image>
				<image src="../../static/my/tools/班车时刻.png" class="small-tools-img-6"></image>
				<image src="../../static/my/tools/社区书籍.png" class="small-tools-img-7"></image>
				<image src="../../static/my/tools/社区共建.png" class="small-tools-img-8"></image>
				<image src="../../static/my/tools/社区期刊.png" class="small-tools-img-9"></image>
				<image src="../../static/my/tools/通知公告.png" class="small-tools-img-10"></image>
			</view>
			<view class="small-tools-title">
				<text class="small-tools-title-1">咨询服务</text>
				<text class="small-tools-title-2">业务流程</text>
				<text class="small-tools-title-3">服务大厅</text>
				<text class="small-tools-title-4">社区热点</text>
				<text class="small-tools-title-5">社区风景</text>
				<text class="small-tools-title-6">班车时刻</text>
				<text class="small-tools-title-7">社区书籍</text>
				<text class="small-tools-title-8">社区共建</text>
				<text class="small-tools-title-9">社区期刊</text>
				<text class="small-tools-title-10">通知公告</text>
			</view>

		</view>
		<!-- 详细个人 -->
		<view class="example-body">
			<h2 style="position: absolute; left: 20%; top: 15px;" @click="showDrawer('showLeft')">{{nickname}}</h2>
			<text style="position: absolute; left: 20%; top: 45px; font-size: 12px; color: #888888;"
				@click="showDrawer('showLeft')">点击查看个人主页</text>
			<uni-drawer width="430" ref="showLeft" mode="right" :mask-click="false" @change="change($event,'showLeft')">
				<view class="scroll-view">
					<scroll-view class="scroll-view-box" scroll-y="true">

						<view class="close">
							<image class="返回" src="../../static/my/返回键白.png" @click="closeDrawer('showLeft')"></image>
						</view>

						<view class="tupian">
							<image class="背景图" src="../../static/person/背景.jpg"></image>
						</view>

						<!-- 账号情况 -->

						<view class="info">
							<image class="person-userinfo-avatar" :src="avatarUrl" @click="changeAvatar"></image>
							<h2 style="transform: translate(5%, -50%);">{{nickname}}</h2>
							<view class="status-container">
								<view class="status-item">
									<text class="status-number">{{ likes }}</text>
									<text class="status-label">获赞</text>
								</view>
								<text style="font-size: 10px; color: #888888;">|</text>
								<view class="status-item">
									<text class="status-number">{{ followed }}</text>
									<text class="status-label">被关注</text>
								</view>
								<text style="font-size: 10px; color: #888888;">|</text>
								<view class="status-item">
									<text class="status-number">{{ following }}</text>
									<text class="status-label">关注</text>
								</view>
								<image src="../../static/my/认证.png" class="认证"></image>

							</view>
						</view>

						<!-- 编辑个人资料 -->

						<view class="person-info-bottom" @click="showDrawer('infoDrawer')">
							<text class="person-info-text" @click="showDrawer('infoDrawer')">编辑资料</text>
						</view>
						<uni-drawer width="430" ref="infoDrawer" mode="right" :mask-click="false"
							@change="change($event,'infoDrawer')">
							<view class="person-info-scroll-view">
								<scroll-view class="person-info-scroll-view-box" scroll-y="true">
									<view class="close">
										<image class="返回" src="../../static/my/返回键.png"
											@click="closeDrawer('infoDrawer')"></image>
									</view>
								</scroll-view>
							</view>
						</uni-drawer>

						<!-- 二维码 -->

						<view class="person-erwei-bottom" @click="showDrawer('erweiDrawer')">
							<image src="../../static/my/二维码.png" class="person-erwei-img"
								@click="showDrawer('erweiDrawer')"></image>
						</view>
						<uni-drawer width="430" ref="erweiDrawer" mode="right" :mask-click="false"
							@change="change($event,'erweiDrawer')">
							<view class="person-info-scroll-view">
								<scroll-view class="person-info-scroll-view-box" scroll-y="true">
									<view class="close">
										<image class="返回" src="../../static/my/返回键.png"
											@click="closeDrawer('erweiDrawer')"></image>
									</view>
									<view class="二维码-box">
										<image src="../../static/my/我的二维码.png" class="二维码"></image>
										<text class="二维码-nickname">{{nickname}}</text>
									</view>


								</scroll-view>
							</view>
						</uni-drawer>

						<!-- 简介 -->

						<view class="person-info-profile" @click="showDrawer('infoDrawer')">
							<image src="../../static/my/书写.png" class="person-info-profile-img"
								@click="showDrawer('infoDrawer')"></image>
							<text style="position: absolute; left: 15%; top: 1px; font-size: 14px; color: #888888;"
								@click="showDrawer('infoDrawer')">一句话介绍你自己</text>
						</view>
						<uni-drawer width="430" ref="infoDrawer" mode="right" :mask-click="false"
							@change="change($event,'infoDrawer')">
							<view class="person-info-scroll-view">
								<scroll-view class="person-info-scroll-view-box" scroll-y="true">
									<view class="close">
										<image class="返回" src="../../static/my/返回键.png"
											@click="closeDrawer('infoDrawer')"></image>
									</view>
									<image class="person-info-touxiang" :src="avatarUrl" @click="changeAvatar"></image>
									<image src="../../static/my/相机.png" class="person-info-camera"
										@click="changeAvatar"></image>
									<text
										style="font-size:17px;font-weight:bold;position: absolute; left: 25px; top: 175px;">基本资料</text>

									<view class="基本资料">
										<view class="input-group1">
											<text class="label">用户名</text>
											<input class="input" type="text" placeholder="小易热心市民" />

										</view>
										<image src="../../static/my/直线.png" class="line1"></image>
										<view class="input-group2">
											<text class="label">简介</text>
											<input class="input" type="text" placeholder="介绍自己的职业和兴趣" />
										</view>

										<image src="../../static/my/直线.png" class="line2"></image>

										<view>

											<view class="uni-list-cell">
												<view class="uni-list-cell-left">
													性别
												</view>
												<view class="uni-list-cell-db">
													<picker @change="bindPickerChange" :value="index" :range="array">
														<view class="uni-input">{{array[index]}}</view>
													</picker>
												</view>
											</view>

											<image src="../../static/my/直线.png" class="line2"></image>

											<view class="uni-list-cell">
												<view class="uni-list-cell-left">
													生日
												</view>
												<view class="uni-list-cell-db">
													<picker mode="date" :value="date" :start="startDate" :end="endDate"
														@change="bindDateChange">
														<view class="uni-input">{{dateday}}</view>
													</picker>
												</view>
											</view>

											<image src="../../static/my/直线.png" class="line2"></image>
											<text
												style="position: absolute; left: 370px; top: 30px; font-size: 16px; font-weight:bold; color:#007aff;"
												@click="onClick">保存</text>
										</view>

									</view>

								</scroll-view>
							</view>
						</uni-drawer>

						<!-- 动态区 -->

						<view class="tabs">
							<u-tabs lineColor="#007aff" :list="list1"
								:activeStyle="{color: '#020202',fontWeight: 'bold'}" @click="tabsclick"
								:current="tabIndex">
							</u-tabs>
						</view>

					</scroll-view>
				</view>
			</uni-drawer>
		</view>
		<!-- 设置 -->
		<view class="example-body">
			<image class="设置" src="../../static/底部导航/设置.png" @click="showDrawer('showRight')"></image>
			<uni-drawer width="430" ref="showRight" mode="right" :mask-click="false"
				@change="change($event,'showRight')">
				<view class="scroll-view">
					<scroll-view class="setting-box" scroll-y="true">

						<view class="close">
							<image class="返回" src="../../static/my/返回键.png" @click="closeDrawer('showRight')"></image>
						</view>

						<uni-list class="setting-list1">
							<uni-list-item title="查看通讯录好友" note="开启后,他人也可以从通讯录中发现我的账号">
								<template v-slot:footer>
									<switch style="transform:scale(0.8)" />
								</template>
							</uni-list-item>
							<uni-list-item title="水印图片" note="上传的图片在查看原图、保存和分享时,显示水印">
								<template v-slot:footer>
									<switch checked="false" style="transform:scale(0.8)" />
								</template>
							</uni-list-item>
							<uni-list-item title="无图模式" note="使用非Wi-Fi网络时不加载图片">
								<template v-slot:footer>
									<switch style="transform:scale(0.8)" />
								</template>
							</uni-list-item>
							<uni-list-item title="双击赞同" note="点赞同后默认同步至动态">
								<template v-slot:footer>
									<switch checked="false" style="transform:scale(0.8)" />
								</template>
							</uni-list-item>
							<uni-list-item title="夜间模式跟随系统设置" note="夜间模式跟随系统设置的模式保持一致">
								<template v-slot:footer>
									<switch style="transform:scale(0.8)" />
								</template>
							</uni-list-item>
							<uni-list-item showArrow title="字体大小" note="除用户评论以外的字体调节" />
							<uni-list-item showArrow title="视频播放设置" />
						</uni-list>

						<uni-list class="setting-list2">
							<uni-list-item showArrow title="账号与安全" />
							<uni-list-item showArrow title="账号注销" />
						</uni-list>

						<uni-list class="setting-list3">
							<uni-list-item showArrow title="隐私" />
							<uni-list-item showArrow title="已收集个人信息清单" />
							<uni-list-item showArrow title="与第三方共享个人信息清单" />
						</uni-list>

						<uni-list class="setting-list4">
							<uni-list-item>
								<template v-slot:header>
									<text
										style="font-size: 14px; color: #555555;transform: translate(0px,5px);">摇一摇反馈Bug</text>
								</template>
								<template v-slot:footer>
									<switch checked="false" style="transform:scale(0.8)" />
								</template>
							</uni-list-item>
							<uni-list-item>
								<template v-slot:header>
									<text style="font-size: 14px; color: #555555;">清除缓存</text>
								</template>
								<template v-slot:footer>
									<text style="font-size: 14px; color: #555555;">{{缓存}}MB</text>
								</template>
							</uni-list-item>
							<uni-list-item showArrow title="用户体验调研" />
							<uni-list-item showArrow title="关于易社区" />
						</uni-list>
						<uni-list class="setting-list5">
							<uni-list-item>
								<template v-slot:body>
									<text
										style="transform: translate(155px,0px);font-size: 16px;background-color: white;color: #ff5353;"
										@click="out">退出我的账号</text>
								</template>
							</uni-list-item>
						</uni-list>

					</scroll-view>
				</view>
			</uni-drawer>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			const currentDate = this.getDate({
				format: true
			})
			return {
				array: ['男', '女'],
				index: 0,
				dateday: currentDate,
				infoDrawer: false,
				showRight: false,
				showLeft: false,
				erweiDrawer: false,
				avatarUrl: '../../static/person/头像5.JPG',
				icon: '../../static/底部导航/设置.png',
				nickname: '小易热心市民',
				good: 463,
				likes: 17,
				followed: 0,
				following: 16,
				缓存: 366.87,
				list1: [{
					name: '动态',
				}, {
					name: '点赞',
				}],
				tabIndex: 0
			}
		},
		computed: {
			startDate() {
				return this.getDate('start');
			},
			endDate() {
				return this.getDate('end');
			}
		},
		methods: {
			getDate(type) {
				const date = new Date();
				let year = date.getFullYear();
				let month = date.getMonth() + 1;
				let day = date.getDate();

				if (type === 'start') {
					year = year - 60;
				} else if (type === 'end') {
					year = year + 2;
				}
				month = month > 9 ? month : '0' + month;
				day = day > 9 ? day : '0' + day;
				return `${year}-${month}-${day}`;
			},

			bindDateChange: function(e) {
				this.date = e.detail.value
			},

			bindPickerChange: function(e) {
				console.log('picker发送选择改变，携带值为', e.detail.value)
				this.index = e.detail.value
			},

			tabsclick(e) {
				this.currentIndex = e.index;
			},

			showDrawer(e) {
				this.$refs[e].open()
			},

			closeDrawer(e) {
				this.$refs[e].close()
			},

			// 抽屉状态发生变化触发
			change(e, type) {
				console.log((type === 'showLeft' ? '左窗口' : '右窗口') + (e ? '打开' : '关闭'));
				this[type] = e
			},

			onClick(e) {
				console.log('保存修改', e);
				uni.showToast({
					title: '保存成功'
				});
			},

			changeNickname() {
				console.log("点击修改昵称")
				uni.prompt({
					title: '修改昵称',
					message: '请输入新的昵称',
					success: (res) => {
						if (res.confirm && res.value) {
							this.nickname = res.value;
							uni.showToast({
								title: '昵称修改成功'
							});
						}
					}
				});
			},

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

			out() {
				uni.navigateTo({
					url: '../login/login',
				});
			},

		},
		onBackPress() {
			if (this.showRight || this.showLeft || this.infoDrawer || this.erweiDrawer) {
				this.$refs.showLeft.close()
				this.$refs.showRight.close()
				this.$refs.infoDrawer.close()
				this.$refs.erweiDrawer.close()
				return true
			}
		}
	}
</script>

<style>
	.认证 {
		height: 20px;
		width: 20px;
		transform: translate(-195px, 57px);
	}

	.二维码-nickname {
		font-size: 20px;
		color: #373737;
		position: absolute;
		left: 155px;
		top: 560px;
	}

	.二维码 {
		height: 200px;
		width: 200px;
		transform: translate(115px, 316px);
	}

	.返回 {
		height: 20px;
		width: 20px;
		left: 75%;
		transform: translate(-300px, 30px);
		position: relative;
	}

	.设置 {
		height: 25px;
		width: 25px;
		left: 75%;
		transform: translate(55px, -220px);
	}

	.small-tools-title {
		height: 120px;
		width: 400px;
		position: absolute;
		left: 15px;
		top: 200px;
	}

	.small-tools-title-1,
	.small-tools-title-2,
	.small-tools-title-3,
	.small-tools-title-4,
	.small-tools-title-5,
	.small-tools-title-6,
	.small-tools-title-7,
	.small-tools-title-8,
	.small-tools-title-9,
	.small-tools-title-10 {
		margin-right: 16px;
		font-size: 12px;
		color: #888888;
	}

	.small-tools {
		height: 120px;
		width: 400px;
		position: absolute;
		left: 15px;
		top: 200px;
	}

	.small-tools-img-1,
	.small-tools-img-2,
	.small-tools-img-3,
	.small-tools-img-4,
	.small-tools-img-5,
	.small-tools-img-6,
	.small-tools-img-7,
	.small-tools-img-8,
	.small-tools-img-9,
	.small-tools-img-10 {
		height: 30px;
		width: 30px;
	}

	.userinfo {
		margin: 35px 0px;
		display: flex;
		align-items: center;
	}

	button {
		background-color: ;
		border-radius: 5px;
	}

	.userinfo-avatar {
		height: 64px;
		width: 64px;
		left: 15%;
		transform: translate(-75%, 10%);
		border-radius: 50%;
	}

	.auth-button {
		height: 10px;
		width: 75px;
		display: flex;
		align-items: center;
		justify-content: center;
		background-color: #f0f0f0;
		border-radius: 15px;
		padding: 5px 10px;
		border: 1px solid #b2b2b2;
		transform: translate(15px, -10px);
	}

	.auth-text {
		font-size: 12px;
		color: #646464;
		white-space: nowrap;
	}

	.person-info-bottom {
		height: 20px;
		width: 50px;
		display: flex;
		align-items: center;
		justify-content: center;
		background-color: #f0f0f0;
		border-radius: 15px;
		padding: 5px 10px;
		transform: translate(280px, -190px);
	}

	.person-info-text {
		font-size: 12px;
		color: #525252;
		white-space: nowrap;
	}

	.person-erwei-bottom {
		height: 20px;
		width: 20px;
		display: flex;
		align-items: center;
		justify-content: center;
		background-color: #f0f0f0;
		border-radius: 15px;
		padding: 5px 5px;
		transform: translate(360px, -220px);
	}

	.person-erwei-img {
		height: 15px;
		width: 15px;
	}

	.person-info-profile {
		display: flex;
		background-color: #ffffff;
		transform: translate(20px, -200px);
		height: 40px;
		width: 225px;
	}

	.person-info-profile-img {
		height: 18px;
		width: 18px;
	}

	.example-body {
		padding: 10px;
	}

	.scroll-view {
		/* #ifndef APP-NVUE */
		width: 100%;
		height: 100%;
		/* #endif */
		flex: 1
	}

	.scroll-view-box {
		flex: 1;
		position: absolute;
		top: 0;
		right: 0;
		bottom: 0;
		left: 0;
	}

	.person-info-scroll-view-box {
		flex: 1;
		position: absolute;
		top: 0;
		right: 0;
		bottom: 0;
		left: 0;
	}

	.setting-box {
		flex: 1;
		position: absolute;
		top: 0;
		right: 0;
		bottom: 0;
		left: 0;
		transform: translate(0%, 0px);
	}

	.uni-list {
		transform: translate(0%, 30%);
	}

	.tupian {
		height: 241.875px;
		width: 430px;
	}

	.背景图 {
		height: 241.875px;
		width: 430px;
		transform: translate(0%, -10%);
		position: relative;
		z-index: -1;
	}

	.info {
		transform: translate(0%, -25%);
		background-color: white;
		height: 225px;
		width: 430px;
		border-radius: 16px;
	}

	.person-userinfo-avatar {
		height: 96px;
		width: 96px;
		left: 15%;
		transform: translate(-50%, -25%);
		border-radius: 50%;
		border: 3px solid #ffffff;
	}

	.person-info-touxiang {
		height: 80px;
		width: 80px;
		left: 15%;
		transform: translate(-40px, 45px);
		border-radius: 50%;
	}

	.person-info-camera {
		height: 30px;
		width: 30px;
		left: 15%;
		transform: translate(-95px, 20px);
		border-radius: 50%;
	}

	.status-container {
		display: flex;
		justify-content: space-around;
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
		margin-right: 5px;
	}

	.status-label {
		font-size: 12px;
		color: #666;
	}

	.my-info {
		display: flex;
		justify-content: space-around;
		background-color: #ffffff;
		transform: translate(0px, 0px);
		height: 40px;
		width: 430px;
		align-items: center;
	}

	.my-info-item {
		text-align: center;
	}

	.my-info-item-num {
		font-size: 12px;
		font-weight: bold;
		margin-right: 5px;
		color: #333;
	}

	.my-info-item-label {
		font-size: 12px;
		color: #888888;
	}

	.setting-list1 {
		transform: translate(0px, 50px);
	}

	.setting-list2 {
		transform: translate(0px, 75px);
	}

	.setting-list3 {
		transform: translate(0px, 100px);
	}

	.setting-list4 {
		transform: translate(0px, 125px);
	}

	.setting-list5 {
		transform: translate(0px, 150px);
	}

	.tabs {
		display: flex;
		align-items: center;
		justify-content: center;
		transform: translate(0px, -150px);
	}

	.small-tools-img-1 {
		transform: translate(25px, 15px);
	}

	.small-tools-img-2 {
		transform: translate(75px, 15px);
	}

	.small-tools-img-3 {
		transform: translate(125px, 15px);
	}

	.small-tools-img-4 {
		transform: translate(175px, 15px);
	}

	.small-tools-img-5 {
		transform: translate(225px, 15px);
	}

	.small-tools-img-6 {
		transform: translate(-125px, 75px);
	}

	.small-tools-img-7 {
		transform: translate(-75px, 75px);
	}

	.small-tools-img-8 {
		transform: translate(-25px, 75px);
	}

	.small-tools-img-9 {
		transform: translate(25px, 75px);
	}

	.small-tools-img-10 {
		transform: translate(75px, 75px);
	}

	.small-tools-title-1 {
		position: absolute;
		left: 16px;
		top: 45px;
	}

	.small-tools-title-2 {
		position: absolute;
		left: 96px;
		top: 45px;
	}

	.small-tools-title-3 {
		position: absolute;
		left: 176px;
		top: 45px;
	}

	.small-tools-title-4 {
		position: absolute;
		left: 256px;
		top: 45px;
	}

	.small-tools-title-5 {
		position: absolute;
		left: 336px;
		top: 45px;
	}

	.small-tools-title-6 {
		position: absolute;
		left: 16px;
		top: 105px;
	}

	.small-tools-title-7 {
		position: absolute;
		left: 96px;
		top: 105px;
	}

	.small-tools-title-8 {
		position: absolute;
		left: 176px;
		top: 105px;
	}

	.small-tools-title-9 {
		position: absolute;
		left: 256px;
		top: 105px;
	}

	.small-tools-title-10 {
		position: absolute;
		left: 336px;
		top: 105px;
	}

	.基本资料 {
		padding: 25px;
	}

	.input-group1,
	.input-group2 {
		display: flex;
		align-items: center;
		transform: translate(0px, 70px);
	}

	.label {
		width: 80px;
	}

	.input {
		flex: 1;
		padding: 5px;
		border-radius: 4px;
	}

	.line1,
	.line2 {
		height: 10px;
		width: 380px;
		transform: translate(0px, 55px);
	}

	.uni-list-cell {
		transform: translate(0px, 60px);
	}

	.uni-list-cell-db {
		transform: translate(84px, 0px);
	}

	.uni-list-cell-left {
		transform: translate(0px, 20px);
	}
</style>