<template>
	<view class="all">
		<uni-forms class="reg">
			<uni-forms-item label="手机号" required class="item">
				<uni-easyinput v-on:blur="resname(user_name)" type="text" v-model="user_name" placeholder="请输入手机号码"
					maxlength="11" class="reg-input"></uni-easyinput>
			</uni-forms-item>
			<uni-forms-item label="密码" required class="item">
				<uni-easyinput @blur="respassword(password)" type="text" password="true" v-model="password"
					placeholder="请输入密码" maxlength="16" class="reg-input"></uni-easyinput>
			</uni-forms-item>
			<button class="reg-btn" type="default" @tap="finishreg()">完成注册</button>
		</uni-forms>
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
			finishreg() {
				if (this.testname == 0 && this.tespassword == 0) { //&&——与符号,表示前后两个条件都要符合才行。
					uni.showToast({
						title: '格式都对',
						icon: 'none'
					});
					uniCloud.callFunction({
						name: "register",
						data: {
							"user_name": this.user_name,
							"password": this.password,
						},
						success: (res) => {
							console.log("对register函数发送请求成功", res)
							var status = res.result.status
							if (status == 0) {
								uni.showToast({
									title: '注册成功',
									icon: 'none'
								});
							} else {
								uni.showToast({
									title: '用户名重复',
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
			}
		}
	}
</script>

<style>
	.reg-btn {
		margin-top: 10px;
		width: 55%;
		height: 90rpx;
		line-height: 90rpx;
		background: skyblue;
		border-radius: 50rpx;
		color: white;
	}

	.reg-input {
		padding: 10px;
		background-color: #fff;
	}

	.reg {
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.item {
		display: flex;
		flex-direction: row;
		align-items: center;
	}
</style>