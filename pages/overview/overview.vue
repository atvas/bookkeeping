<template>
	<view class="over-body">
		<u-navbar :is-back="false" title="记账本"></u-navbar>
		<view class="content">
			{{msg}}
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				msg : '这是概览页面'
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	uni-page-wrapper{
		background-color: #FFFFFF;
	}
</style>
