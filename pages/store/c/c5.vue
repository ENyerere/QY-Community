<template>
	<uni-card>
			<uni-section title="水电维修" type="line" class="fee">
				<uni-list class="list">
					<uni-list-item title="用电故障" link="redirectTo" to='./c5-1' class="content"></uni-list-item>
					<uni-list-item title="生活用水" link="redirectTo" to='./c5-2' class="content"></uni-list-item>
				</uni-list>
			</uni-section>
	</uni-card>
</template>

<script>
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