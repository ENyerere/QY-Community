<template>
	<uni-card>
			<uni-section title="缴费服务" type="line" class="fee">
				<uni-list class="list">
					<uni-list-item title="我要缴费" link="redirectTo" to='./c1-1' class="content"></uni-list-item>
				</uni-list>
			</uni-section>
	</uni-card>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {
			
		}
	}
</script>

<style>
	.fee {
		width: 100%;
		height: 300px;
		padding: 0;
	}
	.content{
		border-left: 1px solid rgba(0, 0, 0, 0.1);
		border-right: 1px solid rgba(0, 0, 0, 0.1);
	}
	
</style>