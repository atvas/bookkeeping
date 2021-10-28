<template>
	<view>
		<u-navbar :is-back="false" title="首页"></u-navbar>
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

</style>
