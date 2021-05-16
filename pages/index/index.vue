<template>
	<view class="container">
		<view class="coupon" ref="coupon">
			<view class="item" v-for="(v, i) in couponList" @click="toCoupon(i)" :key="i">
				<view class="top">
					<view class="left">
						<view class="content">
							<image :src="v.icon" class="icon" mode="widthFix" />
							<view class="name">{{ v.name }}</view>
						</view>
						<view class="text">天天可领</view>
					</view>
					<view class="right">立即领取</view>
				</view>
				<view class="bottom"><image :src="v.bannerPic" mode="widthFix" /></view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			couponList: [
				{
					name: '饿了么红包',
					icon: '/static/ele.png',
					bannerPic: '/static/ele_banner.png',
					url: 'https://h5.ele.me/ant/qrcode?open_type=miniapp&url_id=35&inviterId=61764a1&_ltracker_f=tjyj2_app_grzx2&chInfo=ch_share__chsub_CopyLink',
					minapp: {
						appid: 'wxece3a9a4c82f58c9',
						path: '/taoke/pages/shopping-guide/index?scene=dxEE1ou'
					}
				},
				{
					name: '美团外卖红包',
					icon: '/static/meituan.png',
					bannerPic: '/static/meituan_banner.png',
					url:'https://dpurl.cn/GfwwwGTz',
					minapp: {
						appid: 'wxde8ac0a21135c07d',
						path: '/index/pages/h5/h5?weburl=https%3A%2F%2Fdpurl.cn/GfwwwGTz'
					}
				}
			]
		};
	},
	onLoad(e) {
		
	},
	onShareAppMessage(res) {
		var messages = [{
			title: '领红包点外卖，享优惠',
			path: '/pages/index/index'
		},{
			title: '外卖好食节！狂撒4场红包雨，抢18元大红包！',
			path: '/pages/index/index'
		}];
		return messages[Math.floor(Math.random()*messages.length)];
	},
	methods: {
		toCoupon(i){
			if(this.couponList[i].minapp){
				wx.navigateToMiniProgram({
				  appId: this.couponList[i].minapp.appid,
				  path: this.couponList[i].minapp.path,
				  success(res) {
					// 打开成功
				  }
				})
			}
		}
	}
};
</script>

<style lang="scss">
page {
	background-color: #f8f8f8;
}
.container {
	font-size: 14px;
	line-height: 24px;
	position: relative;
	.coupon {
		.item {
			background-color: #ffffff;
			margin: 30rpx;
			border-radius: 10rpx;
			padding: 0 30rpx 30rpx 30rpx;
			.top {
				height: 116rpx;
				display: flex;
				align-items: center;
				justify-content: space-between;
				.left {
					height: 116rpx;
					width: 400rpx;
					display: flex;
					align-items: center;
					justify-content: space-between;
					.content {
						width: 100%;
					}
					.icon {
						display: inline-block;
						vertical-align: bottom;
						width: 52rpx;
						height: auto;
					}
					.name {
						text-align: left;
						display: inline-block;
						vertical-align: bottom;
						font-size: 34rpx;
						color: #000;
						line-height: 50rpx;
						font-weight: bold;
						margin-left: 15rpx;
					}
					.text {
						width: 150rpx;
						height: 38rpx;
						line-height: 38rpx;
						text-align: center;
						font-size: 24rpx;
						color: #61300e;
						background: linear-gradient(90deg, #f9db8d, #f8d98a);
						border-radius: 6rpx;
					}
				}

				.right {
					width: 170rpx;
					height: 60rpx;
					border-radius: 30rpx;
					background: linear-gradient(90deg, #ec6f43, #ea4a36);
					color: #fff;
					font-size: 28rpx;
					line-height: 60rpx;
					text-align: center;
				}
			}

			.bottom {
				height: auto;
				width: 100%;
				image {
					display: block;
					width: 100%;
					height: auto;
				}
			}
		}
	}
}
</style>
