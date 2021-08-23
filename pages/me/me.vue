<template>
	<view class="me">
		<view class="top">
			<image src='https://z3.ax1x.com/2021/05/28/2FSPAS.png'></image>
		</view>
		<view class="user">

			<!-- #ifdef MP-TOUTIAO -->
			<image :src=avatarUrl></image>
			<text class="id">{{nickName}}</text>
			<!-- #endif -->

			<!-- #ifdef H5 -->
			<image src='../../static/routw.png'></image>
			<text class="id">Back</text>
			<!-- #endif -->

		</view>


		<view class="list">
			<view class="wrapper">
				<view class="info" @click="openDouyinOrderList()">
					<view class="info-left">
						<view class="cuIcon-text"></view>
						<text>我的订单</text>
					</view>
					<view class="info-right">
						<view class="cuIcon-right"></view>
					</view>
				</view>
				<view class="info" @click="showFavoriteGuide()">
					<view class="info-left">
						<view class="cuIcon-favor"></view>
						<text>关注我们</text>
					</view>
					<view class="info-right">
						<view class="cuIcon-right"></view>
					</view>
				</view>
				<view class="info" @click="aboutUs()">
					<view class="info-left">
						<view class="cuIcon-info"></view>
						<text>关于我们</text>
					</view>
					<view class="info-right">
						<view class="cuIcon-right"></view>
					</view>
				</view>
				<view class="info" @click="tapMakePhoneCall()">
					<view class="info-left">
						<view class="cuIcon-phone"></view>
						<text>联系客服</text>
					</view>
					<view class="info-right">
						<view class="num">0816-77777777</view>
						<view class="cuIcon-right"></view>
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
				avatarUrl: '',
				nickName: '',

			}
		},
		methods: {
			//#ifdef MP-TOUTIAO
			openDouyinOrderList(e) {
				tt.openDouyinOrderList({
					success(res) {
						console.log("调用成功", res);
					},
					fail(res) {
						console.log("调用失败", res);
					},
				});
			},
			tapMakePhoneCall() {
			    tt.makePhoneCall({
			      phoneNumber: "0816-77777777",
			      success(res) {
			        // 调用成功 makePhoneCall:ok
			        console.log("调用成功", res.errMsg);
			      },
			      fail(res) {
			        // 调用失败 makePhoneCall:fail
			        console.log("调用失败", res.errMsg);
			      },
			    });
			 },
			showFavoriteGuide(){
				tt.showFavoriteGuide({
				  type: "bar",
				  content: "一键添加到「我的小程序」",
				  position: "bottom",
				  success(res) {
				    console.log("引导组件展示成功", res);
				  },
				  fail(err) {
				    console.log("引导组件展示失败", err);
				  },
				});
			},
			
			//#endif
			 aboutUs(){
				 uni.navigateTo({
				  url:'aboutUs/aboutUs'
				 })
			 },
		},
		onLoad() {
			//#ifdef MP-TOUTIAO
			tt.login({
				force: true,
				success: (res) => {
					console.log(`login 调用成功`);
				},
				fail: (res) => {
					console.log(`login 调用失败`);
				},
			});

			tt.getUserInfo({
				withCredentials: true,
				success: (res) => {
					console.log(`getUserInfo 调用成功`);
					this.avatarUrl = res.userInfo.avatarUrl;
					this.nickName = res.userInfo.nickName;

				},
				fail: (res) => {
					console.log(`getUserInfo 调用失败`);
				},
			});
			

			//#endif

		},
		onShow() {
			//#ifdef MP-TOUTIAO
			tt.checkSession({
				success: (res) => {
					console.log(`session 未过期`);
				},
				fail: (res) => {
					console.log(`session 已过期，需要重新登录`);
					tt.login({
						success: (res) => {
							console.log("登录成功", res);
						},
						fail: (err) => {
							console.log("登录失败", err);
						},
					});
				},
			});
			//#endif

		}
	}
</script>

<style lang="scss">
	.me {
		position: relative;

		.top {
			image {
				width: 750rpx;
				height: 500rpx;
				margin-bottom: 80rpx;
			}
		}

		.user {
			display: flex;
			height: 120rpx;
			position: absolute;
			top: 385rpx;
			left: 30rpx;

			image {
				width: 120rpx;
				height: 120rpx;
				border-radius: 1000rpx;
			}

			text {
				display: block;
				font-size: 30rpx;
				line-height: 30rpx;
				color: #EEEEEE;
				margin-left: 30rpx;
				margin-top: 45rpx;
			}
		}

		.list {
			.wrapper {
				.info {
					display: flex;
					justify-content: space-between;
					height: 80rpx;
					margin: 50rpx 35rpx 0 35rpx;
					border-bottom: 1px solid rgba(238, 238, 238, 0.1);

					.info-left {
						display: flex;
						font-size: 32rpx;
						line-height: 32rpx;
						color: #EEEEEE;

						view {
							margin-right: 20rpx;
							font-size: 40rpx;
						}
					}

					.info-right {
						display: flex;
						font-size: 26rpx;
						line-height: 30rpx;
						color: #EEEEEE;

						.num {
							color: #8B8C91;
							font-size: 30rpx;
							line-height: 30rpx;
							margin-right: 10rpx;
						}
					}
				}
			}

		}
	}
</style>
