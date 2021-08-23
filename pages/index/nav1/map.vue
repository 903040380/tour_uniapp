<template>
	<view>
	<map :latitude="latitude" :longitude="longitude"></map>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				latitude:0,
				longitude:0
			}
		},
		methods: {
			getLocation(){
				uni.getLocation({
				    type: 'wgs84',
				    success:(res) =>{
						this.latitude=res.latitude
						this.longitude=res.longitude
				        console.log('当前位置的经度：' + res.longitude);
				        console.log('当前位置的纬度：' + res.latitude);
				    }
				})
			}
			
		},
		onLoad() {
			this.getLocation()
		}
	}
</script>

<style>
	map{
		width: 750rpx;
		height: 1400rpx;
		margin: auto 0;
	}
</style>
