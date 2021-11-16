<template>
	
	<view>
		<view class="u-page">
			<u-navbar :is-back="false" title="明细"></u-navbar>
			<!-- 所有内容的容器 -->
			<view class="content">
				<u-empty text="内容为空" mode="list"></u-empty>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
	}
</script>

<style lang="scss" scoped>
	.content{
		margin-top: 500rpx;
	}
</style>
