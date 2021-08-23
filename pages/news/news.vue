<template>
	<view class="news">

		<view class="article">
			<view class="title">
				<view class="title-left">热门文章</view>
			</view>
			<view class="info">
				<view class="info-left">
					
					<view class="wrapper" @click="newsClick">
						<image src="../../static/new1.png"></image>
						<text>上方山温暖新春季邀请您一起同花瓣游目的！</text>
						<view class="author">
							<image src="../../static/微信截图_20210531095501.png"></image>
							<text>苏州市文化和旅游厅</text>
						</view>
					</view>
					
					<view class="wrapper" @click="newsClick">
						<image src="../../static/new1.png"></image>
						<text>上方山温暖新春季邀请您一起同花瓣游目的！啊啊啊啊啊</text>
						<view class="author">
							<image src="../../static/微信截图_20210531095501.png"></image>
							<text>苏州市文化和旅游厅</text>
						</view>
					</view>
					<view class="wrapper" @click="newsClick">
						<image src="../../static/new1.png"></image>
						<text>上方山温暖新春季邀请您一起同花瓣游目的！啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊</text>
						<view class="author">
							<image src="../../static/微信截图_20210531095501.png"></image>
							<text>苏州市文化和旅游厅</text>
						</view>
					</view>
					<view class="wrapper" @click="newsClick">
						<image src="../../static/new1.png"></image>
						<text>上方山温暖新春季邀请您一起同花瓣游目的！啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊</text>
						<view class="author">
							<image src="../../static/微信截图_20210531095501.png"></image>
							<text>苏州市文化和旅游厅</text>
						</view>
					</view>
					<view class="wrapper" @click="newsClick">
						<image src="../../static/new1.png"></image>
						<text>上方山温暖新春季邀请您一起同花瓣游目的！</text>
						<view class="author">
							<image src="../../static/微信截图_20210531095501.png"></image>
							<text>苏州市文化和旅游厅</text>
						</view>
					</view>
							
									
				</view>
				
				<view class="info-right">
					
					
					
					<view class="wrapper" @click="newsClick">
						<image src="../../static/new1.png"></image>
						<text>上方山温暖新春季邀请您一起同花瓣游目的方山温暖新春季邀请您一起同花瓣游目的！</text>
						<view class="author">
							<image src="../../static/微信截图_20210531095501.png"></image>
							<text>苏州市文化和旅游厅</text>
						</view>
					</view>
					
					<view class="wrapper" @click="newsClick">
						<image src="../../static/new1.png"></image>
						<text>上方山温暖新春季邀请您一起同花瓣游目的！花瓣游花瓣游花瓣游</text>
						<view class="author">
							<image src="../../static/微信截图_20210531095501.png"></image>
							<text>苏州市文化和旅游厅</text>
						</view>
					</view>
					<view class="wrapper" @click="newsClick">
						<image src="../../static/new1.png"></image>
						<text>上方山温暖新春季邀请您一起同花瓣游目的！花瓣游啊啊啊啊花瓣游啊</text>
						<view class="author">
							<image src="../../static/微信截图_20210531095501.png"></image>
							<text>苏州市文化和旅游厅</text>
						</view>
					</view>
					<view class="wrapper" @click="newsClick">
						<image src="../../static/new1.png"></image>
						<text>上方山温暖新春季邀请您一起同花瓣游目的！花瓣游花瓣</text>
						<view class="author">
							<image src="../../static/微信截图_20210531095501.png"></image>
							<text>苏州市文化和旅游厅</text>
						</view>
					</view>
					<view class="wrapper" @click="newsClick">
						<image src="../../static/new1.png"></image>
						<text>上方山温暖新春季邀请您一起同花瓣游目的！方山温暖新春季邀请您一起同花瓣游目的方山温暖新春季邀请您一起同花瓣游目的</text>
						<view class="author">
							<image src="../../static/微信截图_20210531095501.png"></image>
							<text>苏州市文化和旅游厅</text>
						</view>
					</view>
							
									
				</view>
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
		newsClick(){
				uni.navigateTo({
					url:'/pages/news/article/article'
				})
			}
		}
	}
</script>

<style lang="scss">
	.article {
		
		.title {
			margin: 20rpx 25rpx 30rpx 25rpx;
			
			.title-left {
				font-size: 32rpx;
				line-height: 32rpx;
				color: #EEEEEE;
			}
		}
		
		
		.info{
			display: flex;
			justify-content: space-between;
			width: 700rpx;
			height: 2000rpx;
			margin: 0 auto;
			
			.info-left {
				width: 345rpx;
			
				.wrapper {
					width: 345rpx;
					background-color: #24262F;
					border-radius: 15px;
					margin-bottom: 20rpx;
					image {
						width: 345rpx;
						height: 150rpx;
						margin-bottom: 10rpx;
						border-radius: 15px;
					}
			
					text {
						display: inline-block;
						font-size: 26rpx;
						line-height: 50rpx;
						margin:0 15rpx ;
						color: #EEEEEE;
					}
			
					.author {
						image{
							margin:30rpx 15rpx 0 15rpx;
							width: 24rpx;
							height: 24rpx;
						}
						text{
							color: #EEEEEE;
							font-size: 24rpx;
							line-height: 70rpx;
						}
					}
				}
			}
			
			
			
			.info-right {
				width: 345rpx;
			
				.wrapper {
					width: 345rpx;
					background-color: #24262F;
					border-radius: 15px;
					margin-bottom: 20rpx;
					image {
						width: 345rpx;
						height: 150rpx;
						margin-bottom: 10rpx;
						border-radius: 15px;
					}
			
					text {
						display: inline-block;
						font-size: 26rpx;
						line-height: 50rpx;
						margin:0 15rpx ;
						color: #EEEEEE;
					}
			
					.author {
						image{
							margin:30rpx 15rpx 0 15rpx;
							width: 24rpx;
							height: 24rpx;
						}
						text{
							color: #EEEEEE;
							font-size: 24rpx;
							line-height: 70rpx;
						}
					}
				}
			}
			
			
		}
		
	}
</style>
