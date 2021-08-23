<template>
	
	<view class="hotel">
		<view class="title">
			<view class="title-left">
				<view class="title-click"  @click="unFold1()">
					<view class="title-name">全省</view>
					<view class="cuIcon-unfold arrow"></view>
				</view>
				<view class="blank" v-show="flag1">
					<view @click="gethotelIndex(0)">全省</view>
					<view @click="gethotelIndex(1)">张家港市</view>
					<view @click="gethotelIndex(2)">常熟市</view>
					<view @click="gethotelIndex(3)">太仓市</view>
					<view @click="gethotelIndex(4)">昆山市</view>
					<view @click="gethotelIndex(5)">吴江区</view>
					<view @click="gethotelIndex(6)">吴中区</view>
					<view @click="gethotelIndex(7)">相城区</view>
					<view @click="gethotelIndex(8)">姑苏区</view>
					<view @click="gethotelIndex(9)">工业园区</view>
					<view @click="gethotelIndex(10)">高新区</view>
				</view>
			</view>
			<view class="title-middle">
				<view class="title-click" @click="unFold2()">
					<view class="title-name">全部酒店</view>
					<view class="cuIcon-unfold arrow"></view>
				</view>
				<view class="blank" v-show="flag2">
					<view @click="gethotelIndex(11)">五星级酒店</view>
					<view @click="gethotelIndex(12)">休闲场所</view>
					<view @click="gethotelIndex(13)">住宿服务</view>
					<view @click="gethotelIndex(14)">度假村</view>
					<view @click="gethotelIndex(15)">旅馆招待所</view>
					<view @click="gethotelIndex(16)">疗养场所</view>
					<view @click="gethotelIndex(17)">体育休闲</view>
				</view>
			</view>
			<view class="title-right">
				<view class="title-click" @click="unFold3()">
					<view class="title-name">排序</view>
					<view class="cuIcon-unfold arrow"></view>
				</view>
				
				<view class="blank" v-show="flag3">
					<view @click="gethotelIndex(21)">按星级排序</view>
					<view @click="gethotelIndex(22)">按距离排序</view>
				</view>
				
			</view>
		</view>
		<view class="wrapper"  v-for="(item,index) in hotel" :key="index">
			<view class="item" @click="attractionClick()">
				
				<view class="left">
					<image :src="item.img_url"></image>
					<view class="label">
						<text class="sort">民宿</text>
					</view>
				</view>
	
				<view class="right">
					<text class="top">{{item.name}}</text>
					<view class="location">
						<view class="cuIcon-locationfill"></view>
						<view>{{item.region}}</view>
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
				hotel:[],
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
			async gethotel(Flag,Index) {
				console.log(Flag)
				console.log(Index)
				console.log('获取酒店数据');
			
				if(Flag==0){
					const res = await this.$myRequest({
						url: '/get/hotel?Index='+Index
					})
					this.hotel = res.data.hotel;
					console.log('all');
				}else{
					const res = await this.$myRequest({
						url: '/get/hotel?Index='+Index
					})
					this.hotel = res.data.hotel;
					console.log('part');
				}
			
			},
			gethotelIndex(e) {
				console.log('点击')
				console.log(e)
				uni.navigateTo({
				url:'/pages/index/nav1/hotel?Flag=1&Index='+e
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
			this.gethotel(this.Flag,this.Index);
		},
	}
</script>

<style lang="scss">
	.hotel {
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
			
					.label {
						position: absolute;
						z-index: 99;
						top: 115rpx;
						left: 15rpx;
						text-align: center;
						color: #000000;
						width: 70rpx;
						height: 36rpx;
						background-color: #FACE15;
						border-radius: 30px;
						text-align: center;
						font-size: 20rpx;
						line-height: 35rpx;
						
					}
				}
				
				.right{
					
					.top{
						font-size: 28rpx;
						line-height: 40rpx;
						color: #EEEEEE;
					}
					.location{
						display: flex;
						justify-content: space-evenly;
						margin-top: 10rpx;
						width: 120rpx;
						height: 40rpx;
						background-color: #24262F;
						border-radius: 30px;			
						color: #EEEEEE;
						font-size: 20rpx;
						line-height: 20rpx;
									
						view {
							margin: 8rpx 5rpx 0 5rpx;
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

