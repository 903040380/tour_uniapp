<template>
	<view class="navs">
		<view class="nav-item" v-for="(item,index) in nav" :key="index" >
			<view class="wrapper"  v-if="index == 2">
				<!-- <button type="default" data-id="3476724778319146091" bindtap="openGood"></button> -->
				<image :src="item.src"></image>
				<text>{{item.title}}</text>
			</view>
			
			<view class="wrapper" @click="navClick(item.path)" v-else>
				<image :src="item.src"></image>
				<text>{{item.title}}</text>
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
			navClick(path){
				this.$emit('navClick',path)
			},
			//#ifdef MP-TOUTIAO
			// openGood(e) {
			//     tt.openEcGood({
			//       promotionId: e.target.dataset.id,
			//       success(res) {
			//         console.log("调用成功", res);
			//       },
			//       fail(res) {
			//         console.log("调用失败", res);
			//       },
			//     });
			//   },
			//#endif
		},
		props:['nav']
	}
</script>

<style lang="scss">
.navs{
		display: flex;
		.nav-item{
			flex:1;
			text-align: center;
			.wrapper{		
				image{
					margin: 8rpx 20rpx;
					width: 98rpx;
					height: 98rpx;
				}
				
				text{
					display: inline-block;
					font-size: 24rpx;
					color: #8B8C91;
				}
			}
			
			
		}
	}
</style>
