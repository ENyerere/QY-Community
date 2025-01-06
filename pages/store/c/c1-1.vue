<template>
	<uni-card>
		<uni-section title="我要缴费" title-font-size="20px">
			<uni-list class="list">
				<uni-list-item title="绿化养护费用" class="content">
					<template v-slot:footer>
						<switch style="transform(0.6)" />
					</template>
				</uni-list-item>
				<uni-list-item title="清洁卫生费用" class="content">
					<template v-slot:footer>
						<switch style="transform(0.6)" />
					</template>
				</uni-list-item>
				<uni-list-item title="物业共用设施设备、共用部位的日常运行、维护费用" class="content">
					<template v-slot:footer>
						<switch style="transform(0.6)" />
					</template>
				</uni-list-item>
				<uni-list-item title="" class="content">
					<template v-slot:body>
						<view>
							<text>联系人姓名</text>
							<uni-easyinput  placeholder="请输入联系人姓名" class="content" />
						</view>
					</template>
				</uni-list-item>
				<uni-list-item title="" class="content">
					<template v-slot:body>
						<view>
							<text>联系人电话号码</text>
							<uni-easyinput  placeholder="请输入联系电话号码" class="content" />
						</view>
					</template>
				</uni-list-item>
			</uni-list>
		</uni-section>
		<button type="button" class="button" @click="submit">提交</button>
	</uni-card>

</template>

<script>
	export default {
		data() {
			return {

			}
		},


		methods: {
			submit() {
				alert("提交成功")
				setTimeout(() => {
					uni.redirectTo({
						url: '/pages/store/c/c1'
					}), 2000
				})

			}
		}

	};
</script>

<style>
	.content {
		border-left: 1px solid rgba(0, 0, 0, 0.1);
		border-right: 1px solid rgba(0, 0, 0, 0.1);
	}

	.button {
		margin-top: 10px;
		width: 55%;
		height: 90rpx;
		line-height: 90rpx;
		background: skyblue;
		border-radius: 50rpx;
		color: white;
	}
</style>