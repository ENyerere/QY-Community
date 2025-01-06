<template>
	<view class="all">
		<view class="useinfo">
			<block>
				<image class="userinfoImg" src="../../static/person/头像0.png" mode="aspectFill"></image>
				<text>小易热心市民</text>
			</block>
		</view>

		<view class="input-content">


			<view class="input-box">
				<image src="../../static/zh.png" mode="" class="input-bg"></image>
				<input v-on:blur="resname(user_name)" type="text" v-model="user_name" placeholder="请输入手机号码"
					maxlength="11" class="input-phone" />
			</view>
			<view class="input-box">
				<image src="../../static/mm.png" mode="" class="input-bg"></image>
				<input @blur="respassword(password)" type="text" password="true" v-model="password" placeholder="请输入密码"
					maxlength="16" class="input-phone" />
			</view>
		</view>
		<button type="default" class="login-btn" @tap="login()">登录</button>
		<button type="default" class="login-btn" @tap="register()">注册</button>
		<view class="checkbox">
			<checkbox activeBackgroundColor="#1890ff" color="white" style="display: block;">记住我</checkbox>
			<checkbox activeBackgroundColor="#1890ff" color="white" style="margin-top: 10px;">已经阅读并同意<text
					class="user">《用户服务协议》</text></checkbox>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				user_name: "",
				password: "",
				tesname: "",
				tespassword: "",
			}
		},
		methods: {
			resname(val) { //用户名输入框失去焦点触发,根据需求使用正则判断
				var regPhone = (/^(13[0-9]|14[1579]|15[0-3,5-9]|16[6]|17[0123456789]|18[0-9]|19[89])\d{8}$/);
				//手机号码正则判断:各运营商开头前三位+八位,即11位的电话号码。
				if (!regPhone.test(val)) {
					// !表示:与regPhone(正则判断)不符
					this.tesname = 1 //标记判断结果,0——正确;1——错误;
					uni.showToast({
						title: '手机号格式错误',
						icon: 'none'
					});
					return;
				}
				if (regPhone.test(val)) {
					this.testname = 0
					uni.showToast({
						title: '手机号格式正确',
					});
					return;
				}
			},
			respassword(val) { //密码输入框失去焦点触发,密码只要不为空就行
				if (val != "") {
					this.tespassword = 0 //标记判断结果,0——正确;1——错误;
					return;
				}
				if (val == "") {
					this.tespassword = 1
					uni.showToast({
						title: '密码不能为空',
						icon: 'none'
					});
					return;
				}
			},
			login() { //点击登录触发,格式都对就执行,错就提示
				if (this.testname == 0 && this.tespassword == 0) { //&&——与符号,表示前后两个条件都要符合才行。
					uni.showToast({
						title: '格式正确',
						icon: 'none'
					});
					uniCloud.callFunction({
						name: "login",
						data: {
							"user_name": this.user_name,
							"password": this.password,
						},
						success: (res) => {
							console.log("对login函数发送请求成功", res)
							var status = res.result.status
							if (status == 0) {
								uni.switchTab({
									url: "../store/store"
								})
								uni.showToast({
									title: '登录成功',
									icon: 'none'
								});
							}
							if (status == 1) {
								uni.showToast({
									title: '用户名不存在',
									icon: 'none'
								});
							}
							if (status == 2) {
								uni.showToast({
									title: '密码错误',
									icon: 'none'
								});
							}

						},
						fail: (err) => {
							console.log("发送请求失败,错误信息如下", res)
						}
					})
				} else {
					uni.showToast({
						title: '错了,重来',
						icon: 'none'
					});
				}
			},
			register() { //点击注册按钮跳转注册页面
				uni.navigateTo({
					url: "../register/register"
				})
			}
		}
	}
</script>

<style>
	* {
		margin: 0;
		border: 0;
		box-sizing: border-box;
	}

	.useinfo {
		display: flex;
		flex-direction: column;
		align-items: center;
		margin: 35rpx 0;
		border-radius: 50%;
	}

	.userinfoImg {
		width: 230rpx;
		height: 230rpx;
		border-radius: 50%;
		margin: 20rpx;
	}

	.input-content {
		padding: 0 100rpx;
	}

	.input-box {
		position: relative;
		margin: 0 auto;
		padding: 0 50rpx;
		height: 120rpx;
	}

	.input-bg {
		position: absolute;
		left: 0;
		right: 0;
		top: 25rpx;
		bottom: 0;
		width: 40rpx;
		height: 40rpx;
	}

	.input-phone {
		width: 100%;
		height: 80rpx;
		margin-left: 20rpx;
		border-bottom: 1rpx solid black;
	}

	.login-btn {
		margin-top: 10px;
		width: 55%;
		height: 90rpx;
		line-height: 90rpx;
		background: skyblue;
		border-radius: 50rpx;
		color: white;
	}

	.all {
		display: flex;
		flex-direction: column;
		align-items: center;
	}
</style>