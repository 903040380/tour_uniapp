<template>
	<view>
		<swiper circular="true" autoplay="true" interval="3000">
			<swiper-item v-for="item in swipers" :key="item.id">
				<image :src="item.img_src"></image>
			</swiper-item>
		</swiper>
		<view class="title">
			<view class="h1">
				常熟市兵马俑
			</view>
			<view class="label">
				<text class="level">5A景区</text>
				<view>自然风光</view>
				<view>名胜古迹</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				swipers:[],
			}
		},
		methods: {
			async getSwipers() {
				console.log('获取轮播图数据');
			
				const res = await this.$myRequest({
					url: '/get/banner'
				})
				this.swipers = res.data.banner
			
			},
		}
	}
</script>

<style lang="scss">
	swiper {
		width: 750rpx;
		height: 500rpx;
	
		image {
			height: 100%;
			width: 100%;
		}
	}
	.title{
			.h1{
				font-size: 32rpx;
				line-height: 40rpx;
				color: #EEEEEE;
				margin-bottom: 20rpx;
			}
			.label{
				margin-bottom: 35rpx;
				display: flex;
				margin-top: 10rpx;
				.level {
				width: 95rpx;
				height: 36rpx;
				background-color: #2E2B21;
				color: #F0CA14;
				border-radius: 30px;
				text-align: center;
				font-size: 20rpx;
				line-height: 35rpx;
				}
				view {
				width: 105rpx;
				height: 36rpx;
				background-color: #24262F;;
				color: #88888E;
				border-radius: 30px;
				text-align: center;
				font-size: 20rpx;
				line-height: 35rpx;
				margin-left: 10rpx;
				}
			}
	}	
</style>
