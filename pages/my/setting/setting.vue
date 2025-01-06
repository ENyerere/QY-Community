<template>
	<view>
		<view class="container">

			<uni-list>
				<uni-list-item title="头像" note="" showArrow :thumb="avatarUrl" thumb-size="base"
					@click="changeAvatar" />
				<uni-list-item showArrow :title="'昵称:'+nickname" @click="changeNickname" />
				<uni-list-item title="修改密码" link to="/pages/my/modifyPassword/modifyPassword" showArrow></uni-list-item>
			</uni-list>

		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				avatarUrl: '../../../static/person/头像.png',
				nickname: '好名字',
				user: {}
			}
		},
		methods: {

		}
	}
</script>

<style>

</style>