<template>
	<view>
		<swiper circular="true" autoplay="true" interval="3000">
			<swiper-item v-for="item in swipers" :key="item.id">
				<image :src="item.img_src"></image>
			</swiper-item>
		</swiper>
		<view class="wrapper">
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
			<textup :content="info" style="color: #EEEEEE;font-size: 25rpx;"></textup>
			<view class="introduction">
				<view class="h1">
					景点介绍
				</view>
				<view class="location">
					<text>景点地址</text>
					<view class="map">
						<view class="map-left">江苏省常熟市兵马俑坑</view>
						<view class="map-right" @click="getMap">
							<view class="cuIcon-locationfill"></view>
							<text>地图</text>
						</view>
					</view>
				</view>
				
				<view class="time">
					<text>开放时间</text>
					<view>8:00-17:00</view>
				</view>
				
				<view class="phone">
					<text>景区联系电话</text>
					<view>暂无</view>
				</view>
				
				<view class="discount">
					<text>优惠政策</text>
					<textup :content="info" style="color: #EEEEEE;font-size: 25rpx;"></textup>
				</view>
				
				<view class="line">
					<text>交通信息</text>
					<textup :content="info" style="color: #EEEEEE;font-size: 25rpx;"></textup>
					<view class="block"></view>
				</view>
			</view>
		</view>
		<view class="bottom">
			<view class="view" @click="getBuy()">
				<view>查看门票</view>
			</view>
		</view>
	</view>
</template>

<script>
	import sunUniGrand from "@/components/sunui-grand/sunui-grand.vue"
	export default {
		data() {
			return {
				swipers: [],
				info:'国内Android的Push是一个混乱的世界，因为google的push服务器被墙，所以一些国内的安卓手机厂商各自做了自己的推送，比如华为小米魅族等，但还有很多国产手机厂商没有提供官方推送方案。三方独立公司如个推，则提供了独立的push方案。在没有unipush以前，如果只使用三方push，会在很多国产手机上因为节电设置而无法保活push进程，导致无法推送。比如小米手机对三方推送封杀的比较厉害，App退出后很难成功发送push。而如果每个安卓手机的官方push都集成一遍，这么多平台，工作量会非常巨大，管理维护也很麻烦国内Android的Push是一个混乱的世界，因为google的push服务器被墙，所以一些国内的安卓手机厂商各自做了自己的推送，比如华为小米魅族等，但还有很多国产手机厂商没有提供官方推送方案。三方独立公司如个推，则提供了独立的push方案。在没有unipush以前，如果只使用三方push，会在很多国产手机上因为节电设置而无法保活push进程，导致无法推送。比如小米手机对三方推送封杀的比较厉害，App退出后很难成功发送push。而如果每个安卓手机的官方push都集成一遍，这么多平台，工作量会非常巨大，管理维护也很麻烦'
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
			getMap(){
				uni.navigateTo({
					url:'/pages/index/nav1/map'
				})
			},
			getBuy(){
				uni.navigateTo({
					url:'/pages/index/info/buy/buy'
				})
			},
		},
		onLoad() {
			this.getSwipers()
		},
		components:{
			"textup":sunUniGrand
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
	.wrapper{
		margin: 0 25rpx 0 25rpx;
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
		.introduction{
			margin-top: 70rpx;
			margin-bottom: 20rpx;
			.h1{
				font-size: 32rpx;
				line-height: 80rpx;
				color: #EEEEEE;
			}
			.location{
				border-bottom: 1px solid rgba(238, 238, 238, 0.1);
				text{
					color: #88888E;
					line-height: 50rpx;
				}
				.map{
					display: flex;
					justify-content: space-between;
					line-height: 50rpx;
					.map-left{
						color: #EEEEEE;
					}
					.map-right{
						color: #EEEEEE;
						text-align: center;
						line-height: 20rpx;
						text{
							font-size: 23rpx;
						}
					}
				}
				
			}
			.time{
				margin-top: 20rpx;
				border-bottom: 1px solid rgba(238, 238, 238, 0.1);
				text{
					color: #88888E;
					line-height: 50rpx;
				}
				view{
					line-height: 50rpx;
					color: #EEEEEE;
					margin-bottom: 18rpx;
				}
			}
			.phone{
				margin-top: 20rpx;
				border-bottom: 1px solid rgba(238, 238, 238, 0.1);
				text{
					color: #88888E;
					line-height: 50rpx;
				}
				view{
					line-height: 50rpx;
					color: #EEEEEE;
					margin-bottom: 18rpx;
				}
			}
			.discount{
				margin-top: 20rpx;
				padding-bottom: 55rpx;
				border-bottom: 1px solid rgba(238, 238, 238, 0.1);
				text{
					color: #88888E;
					line-height: 50rpx;
				}
			}
			.line{
				margin-top: 20rpx;
				padding-bottom: 55rpx;
				border-bottom: 1px solid rgba(238, 238, 238, 0.1);
				text{
					color: #88888E;
					line-height: 50rpx;
				}
				.block{
					width: 750rpx;
					height: 100rpx;
				}
			}
		}
	}
	.bottom{
		position: fixed;
		bottom: 0;
		width: 750rpx;
		height: 100rpx;
		background-color: #161722;
		.view{
			width: 300rpx;
			height: 80rpx;
			border-radius: 50px;
			background-color: #FE2C55;
			margin: 10rpx auto;
			view{
				font-size: 30rpx;
				line-height: 80rpx;
				color: #EEEEEE;
				margin:0 90rpx;
			}
		}
	}
</style>
