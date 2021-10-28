<template>
	<view>
		<u-navbar back-icon-size="0" back-text="取消" title="记账" :border-bottom="false">
			<view slot='right' class="nav-right" @click="postFrom">完成</view>
		</u-navbar>
		<view class="content">
			<!-- 正文内容 -->
			<u-form :model="form" :error-type="errorType" ref="uForm">
				<u-form-item label="金额" prop="name">
					<u-input v-model="form.name" placeholder="请输入金额" input-align="right" :focus="true" />
				</u-form-item>
				<u-form-item label="日期" prop="time">
					<u-input v-model="form.time" placeholder="请选择日期" @confirm="confirm" input-align="right" @click="show = true"
						:focus="true" />
				</u-form-item>
			</u-form>
			<!-- 时间选择 -->
			<view>
				<u-picker v-model="show" mode="time"></u-picker>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				msg: '这是添加页面',
				form: {
					name: '',
					time: ''
				},
				show: false,
				rules: {
					name: [{
						required: true,
						message: '请输入金额',
						trigger: ['change', 'blur'],
					}]
				},
				errorType: ['toast'] //错误提示
			}
		},
		methods: {
			postFrom() {
				this.$refs.uForm.validate(valid => {
					if (valid) {
						console.log('验证通过');
					} else {
						console.log('验证失败');
					}
				});
			}
		},
		onReady() {
			this.$refs.uForm.setRules(this.rules);
		},
		confirm(e){
			console.log(e)
		}
	}
</script>

<style scoped>
	.nav-right {
		margin-right: 30rpx;
	}

	.content {
		padding: 30rpx 20rpx 0;
	}

	.title {
		color: $u-type-primary;
		text-align: center;
		padding: 20rpx 0 0 0;
	}
</style>
