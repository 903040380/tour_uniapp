<template>
	<view class="index">
		<swiper circular="true" autoplay="true" interval="3000">
			<swiper-item v-for="item in swipers" :key="item.id">
				<image :src="item.img_src"></image>
			</swiper-item>
		</swiper>

		<view class="nav-wrap">
			<navs :nav="nav" @navClick="navItemClick"></navs>
		</view>

		<view class="attraction">

			<view class="title">
				<view class="title-left">热门景区</view>
				<view class="title-right" @click="getMore()">查看更多
				<view class="cuIcon-right"></view>
				</view>
			</view>

			<scroll-view class="info" scroll-x="true">
				<view class="wrapper" v-for="(item,index) in attractions" :key="index" @click="attractionClick">
					<view class="pic">
						<image src="../../static/test.png"></image>
						<view class="location">
							<view class="cuIcon-locationfill"></view>
							<view class="region">{{item.region}}</view>
						</view>
						<view class="level">{{item.level}}A</view>
					</view>
					<text>{{item.name}}</text>
				</view>
			</scroll-view>
		</view>


		<view class="route">
			<view class="title">
				<view class="title-left">热门路线</view>
				<view class="title-right">查看更多<view class="cuIcon-right"></view>
				</view>
			</view>

			<view class="info">
				<view class="wrapper" @click="routeClick">
					<image src="../../static/routw.png"></image>
					<view class="info">
						<view class="top">庐山升龙霸体验+三大景区</view>
						<view class="middle">庐山风景区 -龙哥单体弓大闹天空博物馆民俗浏览-岭山景区</view>
						<view class="bottom">5日 | 自驾游 | 约522公里</view>
					</view>
				</view>

				<view class="wrapper" @click="routeClick">
					<image src="../../static/routw.png"></image>
					<view class="info">
						<view class="top">庐山升龙霸体验+三大景区</view>
						<view class="middle">庐山风景区 -龙哥单体弓大闹天空博物馆民俗浏览-岭山景区</view>
						<view class="bottom">5日 | 自驾游 | 约522公里</view>
					</view>
				</view>
				<view class="wrapper" @click="routeClick">
					<image src="../../static/routw.png"></image>
					<view class="info">
						<view class="top">庐山升龙霸体验+三大景区</view>
						<view class="middle">庐山风景区 -龙哥单体弓大闹天空博物馆民俗浏览-岭山景区</view>
						<view class="bottom">5日 | 自驾游 | 约522公里</view>
					</view>
				</view>
				<view class="wrapper" @click="routeClick">
					<image src="../../static/routw.png"></image>
					<view class="info">
						<view class="top">庐山升龙霸体验+三大景区</view>
						<view class="middle">庐山风景区 -龙哥单体弓大闹天空博物馆民俗浏览-岭山景区</view>
						<view class="bottom">5日 | 自驾游 | 约522公里</view>
					</view>
				</view>

			</view>


		</view>

	</view>
</template>

<script>
	import Navs from '@/components/nav/nav.vue'

	export default {
		data() {
			return {
				swipers: [],
				nav: [{
						src: "../../static/icon1.png",
						title: '景区门票',
						path: '/pages/index/nav1/tickets'
					},
					{
						src: "../../static/icon2.png",
						title: '酒店预订',
						path: '/pages/index/nav1/hotel'
					},
					{
						src: "../../static/icon3.png",
						title: '文旅商店',
					},
					{
						src: "../../static/icon4.png",
						title: '景区地图',
						path: '/pages/index/nav1/map'
					},
					// {
					// 	src: "../../static/icon5.png",
					// 	title: '景区视频',
					// 	path: '/pages/index/nav1/video'
					// }
				],
				attractions:[],
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
			async getAttractions() {
				console.log('获取景区数据');
			
				const res = await this.$myRequest({
					url: '/get/tickets?Index=100'
				})
				this.attractions = res.data.tickets
			
			},
			navItemClick (path){
				console.log(path)
				uni.navigateTo({
					url:path
				})
			},
			
			attractionClick(){
				uni.navigateTo({
					url:'/pages/index/info/attractions/attractions'
				})
			},
			routeClick(){
				uni.navigateTo({
					url:'/pages/index/info/routes/routes'
				})
			},
			getMore(){
				uni.navigateTo({
					url:'/pages/index/nav1/tickets'
				})
			},
			
			//#ifdef MP-TOUTIAO

			//#endif

		},
		onLoad() {
			this.getSwipers()
			this.getAttractions()
		},
		components: {
			"navs": Navs
		}
	}
</script>

<style lang="scss">
	.index {
		swiper {
			width: 750rpx;
			height: 500rpx;

			image {
				height: 100%;
				width: 100%;
			}
		}

		.attraction {
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
					font-size: 24rpx;
					line-height: 40rpx;
					color: #8B8C91;
				}
			}

			.info {
				display: flex;
				white-space: nowrap;
				width: 750rpx;
				margin-left: 20rpx;

				.wrapper {
					margin: 0 8rpx;
					display: inline-block;
					width: 340rpx;
					height: 240rpx;
					background-color: #24262F;
					border-radius: 15px;

					.pic {
						position: relative;

						image {
							width: 340rpx;
							height: 170rpx;
							border-radius: 15rpx;
						}

						.location {
							display: flex;
							justify-content: space-evenly;
							width: 120rpx;
							height: 40rpx;
							background-color: #24262F;
							border-radius: 30px;
							position: absolute;
							z-index: 99;
							top: 115rpx;
							left: 15rpx;
							text-align: right;
							color: #EEEEEE;
							font-size: 20rpx;
							line-height: 20rpx;
							view{
								margin-top: 10rpx;
							}
							.region{
								margin-right: 3rpx;
							}
						}

						.level {
							width: 50rpx;
							height: 40rpx;
							background-color: #FBD313;
							border-radius: 30px;
							position: absolute;
							z-index: 99;
							top: 20rpx;
							right: 20rpx;
							text-align: center;
							font-size: 24rpx;
							line-height: 24rpx;
						}
					}

					text {
						font-size: 28rpx;
						line-height: 60rpx;
						color: #EEEEEE;
						margin-left: 15rpx;
					}
				}


			}
		}
	}

	.route {
		.title {
			display: flex;
			justify-content: space-between;
			margin: 100rpx 25rpx 30rpx 25rpx;

			.title-left {
				font-size: 32rpx;
				line-height: 32rpx;
				color: #EEEEEE;
			}

			.title-right {
				display: flex;
				font-size: 24rpx;
				line-height: 40rpx;
				color: #8B8C91;
			}
		}

		.wrapper {
			width: 700rpx;
			height: 170rpx;
			display: flex;
			justify-content: space-between;
			margin: 20rpx 0 60rpx 40rpx;

			image {
				width: 240rpx;
				height: 170rpx;
				margin-right: 20rpx;
			}

			.info {
				width: 460rpx;

				.top {
					font-size: 26rpx;
					line-height: 40rpx;
					color: #EEEEEE;
				}

				.middle {
					font-size: 22rpx;
					line-height: 30rpx;
					margin-top: 10rpx;
					color: #8B8C91;
				}

				.bottom {
					font-size: 22rpx;
					line-height: 70rpx;
					color: #8B8C91;
				}
			}
		}
	}
</style>
