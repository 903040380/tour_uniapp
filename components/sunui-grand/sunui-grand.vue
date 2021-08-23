<template name='sunui-grand'>
	<view>
		<view v-show="isHide">
			<view class="sunui-grand-hide-bg" :style="'background-color:'+bg+';'">
				<view class="sunui-grand-summary" :style="'-webkit-line-clamp:'+clamp+';'">{{ content }}</view>
				<view class="sunui-grand-show-btn" :style="'top:'+(clamp-1)+'rem;height:'+(clamp/2)+'rem;'" v-show="clamp>=4">
					<view @tap="show" :style="{color:color}">
						<text :style="'border-bottom: 1upx solid '+color+';'">{{expandText}}</text>
					</view>
				</view>
			</view>
		</view>
		<view v-show="!isHide">
			<view class="sunui-grand-show-bg" :style="'background-color:'+bg+';'">
				<view>
					{{ content }}
				</view>
				<view class="sunui-grand-hide-btn" v-show="shinkText!=''">
					<view @tap="hide" :style="{color:color}">
						{{shinkText=='true' || shinkText==true?'':shinkText}}
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	var _self;
	export default {
		data() {
			return {
				isHide: true
			};
		},
		name: 'sunui-grand',
		props: {
			clamp: {
				type: [Number, String],
				default: `4`
			},
			color: {
				type: String,
				default: `#88888E`
			},
			content: {
				type: [String, Object],
				default: ``
			},
			bg: {
				type: String,
				default: `#161722`
			},
			expandText: {
				type: String,
				default: "展开"
			},
			shinkText: {
				type: String,
				default: "收起"
			}
		},
		created() {
			_self = this;
		},
		methods: {
			show() {
				let _this = this;
				_this.isHide = false;
			},
			hide() {
				let _this = this;
				_this.isHide = true;
			}
		}
	}
</script>

<style>
	.sunui-grand-hide-bg {
		background-color: #161722;
		padding: 0;
		padding-bottom: 0;
		position: relative;
	}

	.sunui-grand-show-bg {
		background-color: #161722;
		padding: 0;
	}

	.sunui-grand-summary {
		overflow: hidden;
		text-overflow: clip;
		display: -webkit-box;
		-webkit-box-orient: vertical;
	}

	.sunui-grand-show-btn {
		width: 100%;
		position: absolute;
		left: 0;
		z-index: 0;
		text-align: right;
		padding-top: 0.5rem;
	}

	.sunui-grand-hide-btn {
		text-align: right;
	}
</style>
