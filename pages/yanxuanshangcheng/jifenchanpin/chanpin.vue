<template>
	<view class="index">
		<view class="nav1">
			<u-swiper height='602' :list="bannerList"></u-swiper>
		</view>
		<view class="nav2">
			<view class="tit1">
				<view class="left">
					<image src="/static/image/zu1577.png" class="pic1" mode=""></image>
					<view class="txt1">520积分</view>
				</view>
				<view class="right">规格：20寸</view>
			</view>
			<view class="tit2">SOO行李箱男万向轮拉杆箱耐磨抗摔26英寸A330旅行箱密码箱女商务黑色商务人群</view>
		</view>
		<view class="nav3">
			<view class="tit1">商品详情</view>
		</view>
		<view class="footer">
			<view class="btn">立即兑换</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				isOnShow: true,
				navTitle: '',
				bannerList: [{
						image: 'https://cdn.uviewui.com/uview/swiper/1.jpg',
						title: '昨夜星辰昨夜风，画楼西畔桂堂东'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/2.jpg',
						title: '身无彩凤双飞翼，心有灵犀一点通'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/3.jpg',
						title: '谁念西风独自凉，萧萧黄叶闭疏窗，沉思往事立残阳'
					}
				],
			}
		},
		onLoad(option) {
			console.log(option)
			this.navTitle = option.title;
		},
		onShow() {
			if (!this.isOnShow) {
				return;
			}
		},
		methods: {
			toSeeImg(i, imgArr) {
				this.isOnShow = false;
				uni.previewImage({
					current: i,
					urls: imgArr,
					longPressActions: {
						itemList: ['发送给朋友', '保存图片', '收藏'],
						success: function(data) {
							console.log('选中了第' + (data.tapIndex + 1) + '个按钮,第' + (data.index + 1) +
								'张图片');
						},
						fail: function(err) {
							console.log(err.errMsg);
						}
					}
				});
			},
			toShouyintai() {
				uni.navigateTo({
					url: '/pages/index/search/querendingdan'
				})
				// uni.navigateTo({
				// 	url:'/pages/index/search/shouyintai'
				// })
			},
		}
	}
</script>

<style>
	page {
		background: #F7F8FA;
	}
</style>
<style lang="scss" scoped>
	.index {
		position: relative;
	}

	.nav1 {}
	.nav2{
		width: 726rpx;
		background: #FFFFFF;
		border-radius: 10rpx;
		margin: 18rpx 12rpx;
		padding: 28rpx 26rpx;
		.tit1{
			display: flex;
			align-items: center;
			justify-content: space-between;
			.left{
				display: flex;
				align-items: center;
				.pic1{
					width: 32rpx;
					height: 32rpx;
					margin-right: 12rpx;
				}
				.txt1{
					font-size: 40rpx;
					font-weight: bold;
					color: #FA8677;
				}
			}
			.right{
				font-size: 24rpx;
				font-weight: 400;
				color: #707070;
			}
		}
		.tit2{
			margin-top: 32rpx;
			font-size: 30rpx;
			font-weight: 500;
			line-height: 42rpx;
			color: #BD9E81;
		}
	}
	.nav3{
		margin-left: 12rpx;
		width: 726rpx;
		background: #FFFFFF;
		padding: 28rpx 26rpx;
		border-radius: 10rpx;
		.tit1{
			font-size: 28rpx;
			font-weight: 500;
			color: #BD9E81;
		}
	}
	.footer {
		position: fixed;
		bottom: 0;
		width: 100%;
		height: 140rpx;
		background: #FFFFFF;
		box-shadow: 0rpx 8rpx 28rpx rgba(166, 179, 194, 0.3);
		.btn{
			width: 682rpx;
			height: 84rpx;
			background: #BD9E81;
			border-radius: 44rpx;
			margin-top: 10rpx;
			margin-left: 34rpx;
			font-size: 28rpx;
			font-weight: bold;
			line-height: 84rpx;
			color: #FFFFFF;
			text-align: center;
		}
	}
</style>
