<template>
	<view class="psd-box">
		<uni-section title="请输入旧密码" type="none" padding>
			<uni-easyinput class="uni-mt-5" trim="all" v-model="PSDdata.oldpassword"
				placeholder="请输入旧密码"></uni-easyinput>
		</uni-section>
		<uni-section title="请输入新密码" type="none" padding>
			<uni-easyinput class="uni-mt-5" trim="all" v-model="PSDdata.newpassword"
				placeholder="请输入新密码"></uni-easyinput>
		</uni-section>
		<button @click="modify" class="upPsd">修改密码</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				PSDdata: {
					oldpassword: "",
					newpassword: ""
				}
			};
		},
		methods: {
			modify() {
				var user = uni.getStorageSync("user");
				if (!user || !user.password) {
					uni.showToast({
						title: "用户信息未找到",
						icon: "none"
					});
					return;
				}
				console.log("oldpassword", user.password);
				if (user.password === this.PSDdata.oldpassword) {
					if (this.PSDdata.newpassword === this.PSDdata.oldpassword) {
						uni.showToast({
							title: "新密码不能与旧密码相同",
							icon: "none"
						});
						return;
					}
					user.password = this.PSDdata.newpassword;
					uni.setStorageSync("user", user);
					uni.showToast({
						title: "密码修改成功",
						icon: "success"
					});
					this.PSDdata.oldpassword = "";
					this.PSDdata.newpassword = "";
				} else {
					uni.showToast({
						title: "旧密码错误",
						icon: "none"
					});
				}
			}
		}
	};
</script>

<style scoped>
	.psd-box {
		padding: 20px;
	}

	.upPsd {
		margin-top: 20px;
		background-color: #007aff;
		color: #fff;
		border-radius: 4px;
		padding: 10px;
	}
</style>