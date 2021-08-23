<template>
	<view class="tickets">
		<view class="title">
			<view class="title-left">
				<view class="title-click"  @click="unFold1()">
					<view class="title-name">全省</view>
					<view class="cuIcon-unfold arrow"></view>
				</view>
				<view class="blank" v-show="flag1">
					<view @click="getTicketsIndex(0)">全省</view>
					<view @click="getTicketsIndex(1)">张家港市</view>
					<view @click="getTicketsIndex(2)">常熟市</view>
					<view @click="getTicketsIndex(3)">太仓市</view>
					<view @click="getTicketsIndex(4)">昆山市</view>
					<view @click="getTicketsIndex(5)">吴江区</view>
					<view @click="getTicketsIndex(6)">吴中区</view>
					<view @click="getTicketsIndex(7)">相城区</view>
					<view @click="getTicketsIndex(8)">姑苏区</view>
					<view @click="getTicketsIndex(9)">工业园区</view>
					<view @click="getTicketsIndex(10)">高新区</view>
				</view>
			</view>
			<view class="title-middle">
				<view class="title-click" @click="unFold2()">
					<view class="title-name">全部景点</view>
					<view class="cuIcon-unfold arrow"></view>
				</view>
				<view class="blank" v-show="flag2">
					<view @click="getTicketsIndex(11)">休闲娱乐</view>
					<view @click="getTicketsIndex(12)">公园乐园</view>
					<view @click="getTicketsIndex(13)">名胜古迹</view>
					<view @click="getTicketsIndex(14)">展馆展览</view>
					<view @click="getTicketsIndex(15)">水上项目</view>
					<view @click="getTicketsIndex(16)">温泉泡汤</view>
					<view @click="getTicketsIndex(17)">自然风光</view>
				</view>
			</view>
			<view class="title-right">
				<view class="title-click" @click="unFold3()">
					<view class="title-name">排序</view>
					<view class="cuIcon-unfold arrow"></view>
				</view>
				
				<view class="blank" v-show="flag3">
					<view @click="getTicketsIndex(21)">按星级排序</view>
					<view @click="getTicketsIndex(22)">按价格排序</view>
				</view>
				
			</view>
		</view>
		
		<view class="wrapper"  v-for="(item,index) in tickets" :key="index">
			<view class="item" @click="attractionClick()">
				<view class="left">
					<image :src="item.img_url"></image>
					<view class="location">
						<view class="cuIcon-locationfill"></view>
						<view class="region">{{item.region}}</view>
					</view>
				</view>
			
				<view class="right">
					<text class="top">{{item.name}}</text>
					<view class="label">
						<text class="level">{{item.level}}A景区</text>
						<view>自然风光</view>
						<view>名胜古迹</view>
					</view>
					<view class="price">
					<view>￥{{item.price}}</view>
					<text>起</text>
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
				flag1:false,
				flag2:false,
				flag3:false,
				tickets:[],
				Index:0,
				Flag:0
			}
			
		},
		methods: {
			unFold1(){
				this.flag1=!this.flag1;
				this.flag2=false;
				this.flag3=false;
			},
			unFold2(){
				this.flag2=!this.flag2;
				this.flag1=false;
				this.flag3=false;
			},
			unFold3(){
				this.flag3=!this.flag3;
				this.flag1=false;
				this.flag2=false;
			},
			async getTickets(Flag,Index) {
				console.log(Flag)
				console.log(Index)
				console.log('获取门票数据');
			
				if(Flag==0){
					const res = await this.$myRequest({
						url: '/get/tickets?Index='+Index
					})
					this.tickets = res.data.tickets;
					console.log('all');
				}else{
					const res = await this.$myRequest({
						url: '/get/tickets?Index='+Index
					})
					this.tickets = res.data.tickets;
					console.log('part');
				}
			
			},
			getTicketsIndex(e) {
				console.log('点击')
				console.log(e)
				uni.navigateTo({
				url:'/pages/index/nav1/tickets?Flag=1&Index='+e
				})
			},
			attractionClick(){
				uni.navigateTo({
					url:'/pages/index/info/attractions/attractions'
				})
			},
		},
		onLoad(options){
			if(options.Flag==1){
				this.Flag=options.Flag;
			}
			if(options.Index>0){
				this.Index=options.Index;
			}
			this.getTickets(this.Flag,this.Index);
		},
	}
</script>

<style lang="scss">
	.tickets {
		padding-top: 70rpx;
		.title {
			position: fixed;
			width: 750rpx;
			height: 60rpx;
			background-color: #161722;
			display: flex;
			justify-content: space-between;
			z-index: 9999;
			top: 0;

			.title-left {
				margin-left: 30rpx;
				
				.title-click{
					display: flex;
					.title-name{
						font-size: 28rpx;
						line-height: 40rpx;
						color: #8B8C91;
						margin-right: 10rpx;
					}
					.arrow{
						font-size: 28rpx;
						line-height: 40rpx;
						color: #8B8C91;
						
					}
				}
				.blank{
					position: fixed;
					left: 0;
					width: 750rpx;
					height: 1150rpx;
					background-color: #161722;
					view{
						width: 750rpx;
						font-size: 26rpx;
						line-height: 105rpx;
						color: #EEEEEE;
						margin-left: 30rpx;
					}
				}
			}

			.title-middle {
				margin-left: 30rpx;
				.title-click{
					display: flex;
					.title-name{
						font-size: 28rpx;
						line-height: 40rpx;
						color: #8B8C91;
						margin-right: 10rpx;
					}
					.arrow{
						font-size: 28rpx;
						line-height: 40rpx;
						color: #8B8C91;
						
					}
				}				
				.blank{
					position: fixed;
					left: 0;
					width: 750rpx;
					height: 750rpx;
					background-color: #161722;
					view{
						width: 750rpx;
						font-size: 26rpx;
						line-height: 105rpx;
						color: #EEEEEE;
						margin-left: 30rpx;
					}
				}
			}

			.title-right {
				margin-right: 30rpx;
				.title-click{
					display: flex;
					.title-name{
						font-size: 28rpx;
						line-height: 40rpx;
						color: #8B8C91;
						margin-right: 10rpx;
					}
					.arrow{
						font-size: 28rpx;
						line-height: 40rpx;
						color: #8B8C91;
						
					}
				}

				.blank{
					position: fixed;
					left: 0;
					width: 750rpx;
					height: 250rpx;
					background-color: #161722;
					view{
						width: 750rpx;
						font-size: 26rpx;
						line-height: 105rpx;
						color: #EEEEEE;
						margin-left: 30rpx;
					}
				}
			}
		}
		.wrapper{
			
			.item {
				width: 600rpx;
				height: 200rpx;
				display: flex;
				margin-top: 20rpx;
				.left {
					position: relative;
					margin: 0 30rpx;
					image {
						width: 240rpx;
						height: 160rpx;
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
				}
				
				.right{
					
					.top{
						font-size: 28rpx;
						line-height: 40rpx;
						color: #EEEEEE;
					}
					.label{
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
					.price{
						display: flex;
						margin-top: 35rpx;
						view{
							
							font-size: 35rpx;
							font-weight: 600;
							color: #FE2C55;
							line-height: 40rpx;
						}
						text{
							font-size: 20rpx;
							line-height: 40rpx;
							margin-left: 10rpx;
							color: #88888E;
						}
						
					}
					
					
				}
			}
		}
		
	}
</style>
