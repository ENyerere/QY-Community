<template>
	<uni-card>
		<uni-section title="用电故障" title-font-size="20px">
			<uni-list class="list">
				<uni-list-item title="" class="content">
					<template v-slot:body>
						<view>
							<text>详细地址</text>
							<uni-easyinput type="textarea" autoHeight  placeholder="请输入详细地址"
								class="address" />
						</view>
					</template>
				</uni-list-item>
				<uni-list-item title="" class="content">
					<template v-slot:body>
						<view class="select-group">
							<text>故障描述</text>
							<view class="uni-list-cell">
								<view class="uni-list-cell-left">
									选择故障:
								</view>
								<view class="uni-list-cell-db">
									<picker @change="bindPickerChange" :value="index" :range="array">
										<view class="uni-input">{{array[index]}}</view>
									</picker>
								</view>
							</view>
						</view>
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
				array: ['单户停水：仅一户发生停水', '区域停水：左邻右舍发生停水'],
				index: 0
			}
		},
	
	
		methods: {
			submit() {
				alert("提交成功")
				setTimeout(() => {
					uni.redirectTo({
						url: '/pages/store/c/c5'
					}), 2000
				})
	
			},
			bindPickerChange: function(e) {
				this.index = e.detail.value
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
	
	.address {
		width: 200px;
		height: 100px;
	}
	
	.select-group {
		position: relative;
	}
	
	.uni-list-cell-left {
		margin-right: 10px;
	}
	
	.uni-list-cell-db{
		border: 1px solid rgba(0, 0, 0, 0.1);
		padding: 10px;
		padding-right: 20px;
	}
	
	.uni-list-cell {
		display: flex;
		flex-direction: row;
		align-items: center;
	}
</style>