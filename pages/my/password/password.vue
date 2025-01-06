<template>
	<view>
		<view class="psd-box">
			<uni-section title="请输入旧密码" type="none" padding>
				<uni-eastinput class="old" trim="all" v-model="PSDdata.oldPassword" placeholder="请输入旧密码"></uni-eastinput>
			</uni-section>
			<uni-section title="请输入新密码" type="none" padding>
				<uni-eastinput class="new" trim="all" v-model="PSDdata.newPassword" placeholder="请输入新密码"></uni-eastinput>
			</uni-section>
			<uni-section title="请确认密码" type="none" padding>
				<uni-eastinput class="new1" trim="all" v-model="PSDdata.new1Password" placeholder="确认密码"></uni-eastinput>
			</uni-section>
			<button @click="s" class="toPsd">修改密码</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				PSDdata:{
					oldPassword:'',
					newPassword:'',
					new1Password:''
				}
			}
		},
		methods: {
			s(){
				var user=uni.getStorageSync("user")
				if(user.password===this.PSDdata.oldPassword && this.PSDdata.newPassword===this.PSDdata.new1Password && this.PSDdata.newPassword!=""){
					user.password=this.PSD.newPassword
					uni.setStorageSync("uni",uni)
					uni.showToast({
						title:"密码修改成功"
					})
				}
			}
		}
	}
</script>

<style>

</style>
