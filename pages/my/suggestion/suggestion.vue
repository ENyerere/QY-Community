<template>
	<view>
		<uni-card title="意见反馈">
			<uni-form :model="suggest">
				<uni-easyinput  v-model="suggest.title" placeholder="输入标题" />
				<view class="content">
					<textarea v-model="suggest.body" placeholder="输入内容"></textarea>
				</view>
				<view class="submit">
					<button :type="isSubmitted?'defalut':'primary'" size="mini" form-type="submit" @click="formSubmit">
						{{isSubmitted?'已提交':'提交'}}
					</button>
				</view>
			</uni-form>
		</uni-card>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				suggest:{
					title:'',
					body:''
				},
				isSubmitted:false
			}
		},
		methods: {
			formSubmit(){
				console.log(this.suggest);
				this.isSubmitted=true;
			}
		}
	}
</script>

<style>

</style>
