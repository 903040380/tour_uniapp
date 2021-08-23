<template>
	<view>
		<view class="title">
			<view class="title-left">同程</view>
			<view class="title-right" @click="buy">去买票
				<view class="cuIcon-right"></view>
			</view>
		</view>
		<view class="title">
			<view class="title-left">携程</view>
			<view class="title-right" @click="buy">去买票
				<view class="cuIcon-right"></view>
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
		methods: {
			buy() {
				uni.navigateTo({
					url: '/pages/index/info/buy/web'
				})
			},
		}
	}
</script>

<style lang="scss">
	.title {
		display: flex;
		justify-content: space-between;
		margin: 80rpx 25rpx 30rpx 25rpx;

		.title-left {
			font-size: 32rpx;
			line-height: 32rpx;
			color: #EEEEEE;
		}

		.title-right {
			display: flex;
			font-size: 32rpx;
			line-height: 32rpx;
			color: #EEEEEE;
		}
	}
</style>
