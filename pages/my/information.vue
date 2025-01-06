<template>
	<view>
		<uni-list>
			<uni-list-item title="头像">
				<template v-slot:footer>
					<image class="slot-image" :src="user.tx" mode="widthFix"></image>
				</template>
			</uni-list-item>
			<uni-list-item title="昵称" :right-text="user.name">

			</uni-list-item>
			<uni-list-item title="性别">
				<template v-slot:footer>
					<view>
						<label class="radio">
							<radio value="r1" checked="true" />男
						</label>
						<label class="radio">
							<radio value="r2" />女
						</label>
					</view>
				</template>
			</uni-list-item>
		</uni-list>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				user:{
					name: 'zq',
					tx: '/static/tx.jpg',
				},
			}
		},
		onLoad() {
			var that = this
			uni.request({
				url:"http://127.0.0.1:4523/m1/5517185-5193539-default/imformation",
				success(res){
					console.log(res.data)
					that.user.name=res.data.user.name
					that.user.tx=res.data.user.img
					console.log(that.user)
				},
				fail(err){
					console.log(err)
				}
			})
		},
		methods: {
			
		}
	}
</script>

<style>
	.slot-image {
		/* #ifndef APP-NVUE */
		display: block;
		/* #endif */
		margin-right: 10px;
		width: 30px;
		height: 30px;
		border-radius: 100%;
	}
</style>