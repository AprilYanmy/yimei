<template>
	<view class="index">
		<view class="nav1">
			<view class="tit1">
				<view class="txt1">浙江省</view>
				<u-icon name="arrow-down" color="#000000" size="20"></u-icon>
				<view class="myInp" @click="toSearch">
					<u-icon  @click="toSearch" name="search" color="#000000" size="28"></u-icon>
					<u-input  @click="toSearch" :clearable='false' v-model="searchVal" input-align='center' placeholder='搜索专家/项目/关键词'
						placeholder-style='color: #122106;' type="text" height="60rpx" />
				</view>
			</view>
			<view class="tit2">
				<view class="hot">
					<view class="txt1-1">热搜榜</view>
					<image src="/static/image/lujin1732.png" class="pic" mode=""></image>
				</view>
				<view @click="toSearchResult()" class="txt2">肋骨鼻综合</view>
				<view class="txt2">小眼综合</view>
				<view class="txt2">胸部整形</view>
				<view class="txt2">面部抗衰</view>
			</view>
			<view class="tit3">
				<u-swiper height='320' :list="bannerList"></u-swiper>
			</view>
		</view>
		<view class="nav2">
			<view class="items">
				<view class="item">
					<image src="/static/image/tu188.png" class="pic-item" mode=""></image>
					<view class="txt-item">眼部整形</view>
				</view>
				<view class="item">
					<image src="/static/image/tu189.png" class="pic-item" mode=""></image>
					<view class="txt-item">胸部整形</view>
				</view>
				<view class="item">
					<image src="/static/image/tu190.png" class="pic-item" mode=""></image>
					<view class="txt-item">鼻部整修</view>
				</view>
				<view class="item">
					<image src="/static/image/tu198.png" class="pic-item" mode=""></image>
					<view class="txt-item">玻尿酸</view>
				</view>
				<view class="item">
					<image src="/static/image/tu196.png" class="pic-item" mode=""></image>
					<view class="txt-item">瘦脸针</view>
				</view>
			</view>
			<view class="items items2">
				<view class="item">
					<image src="/static/image/tu193.png" class="pic-item" mode=""></image>
					<view class="txt-item">医学美肤</view>
				</view>
				<view class="item">
					<image src="/static/image/tu194.png" class="pic-item" mode=""></image>
					<view class="txt-item">脂肪填充</view>
				</view>
				<view class="item">
					<image src="/static/image/tu195.png" class="pic-item" mode=""></image>
					<view class="txt-item">半永久妆</view>
				</view>
				<view class="item">
					<image src="/static/image/tu199.png" class="pic-item" mode=""></image>
					<view class="txt-item">激光脱毛</view>
				</view>
				<view class="item">
					<image src="/static/image/tu197.png" class="pic-item" mode=""></image>
					<view class="txt-item">美丽咨询</view>
				</view>
			</view>
			<view class="nav2-1">
				<image src="/static/image/zu1501.png" class="pic3-1" mode=""></image>
				<view class="tit3-1">进口玻尿酸限时8.5折～赶紧加购吧～！</view>
			</view>
		</view>
		<view class="nav3">
			<view class="title">
				<view class="shu"></view>
				<view class="t-txt">修复专区</view>
			</view>
			<view class="items">
				<view class="item" @click="toXiufu(1)">
					<image src="/static/image/mcz193.png" class="pic" mode=""></image>
					<view class="txt">鼻修复</view>
				</view>
				<view class="item" @click="toXiufu(2)">
					<image src="/static/image/mcz192.png" class="pic" mode=""></image>
					<view class="txt">眼修复</view>
				</view>
				<view class="item" @click="toXiufu(3)">
					<image src="/static/image/mcz194.png" class="pic" mode=""></image>
					<view class="txt">胸修复</view>
				</view>
				<view class="item" @click="toXiufu(4)">
					<image src="/static/image/mcz195.png" class="pic" mode=""></image>
					<view class="txt">其他修复</view>
				</view>
			</view>
		</view>
		<view class="nav3 nav4">
			<view class="title">
				<view class="shu"></view>
				<view class="t-txt">专家团队</view>
			</view>
			<scroll-view class="scroll-view" scroll-x style="width: 100%;white-space:nowrap;">
				<view class="itemss">
					<view class="item" @click="toZhuanjiatuandui" v-for="item in 3">
						<image src="/static/image/zzks196.png" class="pic" mode=""></image>
						<view class="right">
							<view class="txt1">
								巴扎嘿<text class="small">院长</text>
							</view>
							<view class="txt2">美容主治医生</view>
							<view class="txt2">医美湘军医生 集团创始人</view>
							<view class="btn">
								<image src="/static/image/lujin1758.png" class="btn-img" mode=""></image>
								<view class="btn-txt">点击预约</view>
							</view>
						</view>
					</view>
				</view>
			</scroll-view>
			<image class="picc" src="/static/image/zu1872.png" mode=""></image>
			<image class="picc2" src="https://cdn.uviewui.com/uview/swiper/2.jpg" mode=""></image>
		</view>
		<view class="nav5">
			<u-tabs-swiper bg-color="#F7F8FA" height='96' font-size="28" gutter="30" inactive-color="#707070"
				bar-height="4" bar-width="64" active-color="#BD9E81" ref="uTabs" :list="list" :current="current"
				@change="tabsChange" :is-scroll="false" swiperWidth="750"></u-tabs-swiper>
			<swiper :style="[{height: height + 'px'}]" :current="swiperCurrent">
				<swiper-item @touchmove.stop class="swiper-item" v-for="(item, index) in list" :key="index">
					<scroll-view scroll-y='true' >
						<view class="nav5Items">
							<!-- {{item.name}} -->
							<!-- 热销 -->
							<template v-if="swiperCurrent == 0">
								<view class="item" @click="toXianqgin" v-for="item in 3">
									<image src="https://img1.baidu.com/it/u=1217556490,2247340394&fm=26&fmt=auto" class="pic" mode=""></image>
									<view class="txt">超光子美白嫩肤一次（活动 特价）</view>
								</view>
							</template>
							<!-- 推荐 -->
							<template v-if="swiperCurrent == 1">

							</template>
							<!-- 口碑 -->
							<template v-if="swiperCurrent == 2">

							</template>
							<!-- 精选 -->
							<template v-if="swiperCurrent == 3">

							</template>
						</view>
					</scroll-view>

				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				searchVal: '',
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
				//
				swiperCurrentIndex: 0,
				height: 0,
				list: [{
					name: '热销'
				}, {
					name: '推荐'
				}, {
					name: '口碑'
				}, {
					name: '精选'
				}],
				// 因为内部的滑动机制限制，请将tabs组件和swiper组件的current用不同变量赋值
				current: 0, // tabs组件的current值，表示当前活动的tab选项
				swiperCurrent: 0, // swiper组件的current值，表示当前那个swiper-item是活动的
			}
		},
		onShow() {
			this.tabsChange(this.current);
		},
		mounted() {
			this.getCurrentSwiperHeight('.nav5Items')
		},
		methods: {
			toSearchResult(){
				uni.navigateTo({
					url:'/pages/search/searchResult'
				})
			},
			toXianqgin(){
				uni.navigateTo({
					url:'/pages/index/search/xiangqin'
				})
			},
			toZhuanjiatuandui(){
				uni.navigateTo({
					url:'/pages/index/zhuanjiatuandui/zhuanjiatuandui'
				})
			},
			toXiufu(i){
				uni.navigateTo({
					url:`/pages/index/xiufu/xiufu?index=${i}`
				})
			},
			toSearch(){
				uni.navigateTo({
					url:'/pages/search/search'
				})
			},
			// tabs通知swiper切换
			tabsChange(index) {
				console.log(index);
				this.swiperCurrent = index;
				this.current = index;
				this.swiperCurrentIndex = index;
				setTimeout(() => {
					this.getCurrentSwiperHeight('.nav5Items')
				}, 200)
			},
			getCurrentSwiperHeight(element) {
				let query = uni.createSelectorQuery().in(this);
				query.selectAll(element).boundingClientRect();
				query.exec((res) => {
					this.height = res[0][this.swiperCurrentIndex].height;
				})
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
	.index {}

	.nav1 {
		width: 750rpx;
		height: 298rpx;
		background: linear-gradient(316deg, #F6A309 0%, #F8B607 22%, #FFD438 42%, #F9C706 51%, #F8CA20 80%, #FECF05 100%);
		padding: 0 36rpx;

		.tit1 {
			padding-top: 32rpx;
			display: flex;
			align-items: center;

			.txt1 {
				font-size: 28rpx;
				font-weight: 500;
				line-height: 40rpx;
				color: #122106;
				margin-right: 14rpx;
			}

			.myInp {
				margin-left: 60rpx;
				padding: 0 24rpx;
				width: 494rpx;
				height: 60rpx;
				background: rgba(255, 255, 255, 0.2);
				border-radius: 50rpx;
				display: flex;
				align-items: center;

				/deep/ .u-input {
					width: 400rpx !important;

					.u-input__input {
						font-size: 24rpx;
						font-weight: 400;
						line-height: 60rpx;
						color: #122106 !important;
					}
				}
			}
		}

		.tit2 {
			margin-top: 30rpx;
			display: flex;
			align-items: center;
			padding: 0 10rpx;
			justify-content: space-between;

			.hot {
				display: flex;
				align-items: center;

				.txt1-1 {
					font-size: 24rpx;
					font-weight: bold;
					line-height: 34rpx;
					color: #122106;
				}

				.pic {
					margin-left: 8rpx;
					width: 20rpx;
					height: 22rpx;
				}
			}

			.txt2 {
				font-size: 24rpx;
				font-weight: 400;
				line-height: 34rpx;
				color: #122106;
			}
		}

		.tit3 {
			margin-top: 34rpx;
		}

	}

	.nav2 {
		background: #FFFFFF;
		padding: 232rpx 38rpx 0 38rpx;

		.items {
			display: flex;
			align-items: center;
			justify-content: space-between;

			.item {
				width: 20%;
				display: flex;
				flex-direction: column;
				align-items: center;

				.pic-item {
					width: 76rpx;
					height: 76rpx;
				}

				.txt-item {
					margin-top: 20rpx;
					font-size: 24rpx;
					font-weight: 400;
					color: #BD9E81;
				}
			}
		}

		.items2.items {
			margin-top: 40rpx;
		}

		.nav2-1 {
			margin-top: 40rpx;
			padding-bottom: 40rpx;
			display: flex;
			align-items: center;
			justify-content: space-between;

			.pic3-1 {
				width: 28rpx;
				height: 28rpx;
				transform: translateX(16rpx);
				margin-right: 16rpx;
			}

			.tit3-1 {
				padding-left: 24rpx;
				width: 612rpx;
				height: 60rpx;
				background: #fff2ee;
				border-radius: 30rpx;
				font-size: 24rpx;
				font-weight: 500;
				color: #FF7C5E;
				line-height: 60rpx;
			}
		}
	}

	.nav3 {
		margin-top: 20rpx;
		width: 750rpx;
		background: #FFFFFF;
		padding: 28rpx 0;

		.title {
			display: flex;
			align-items: center;

			.shu {
				margin-left: 24rpx;
				margin-right: 20rpx;
				width: 6rpx;
				height: 28rpx;
				background: #BD9E81;
			}

			.t-txt {
				font-size: 28rpx;
				font-weight: bold;
				color: #BD9E81;
			}
		}

		.items {
			padding: 0 40rpx;
			margin-top: 36rpx;
			display: flex;
			align-items: center;

			.item {
				width: 25%;
				display: flex;
				flex-direction: column;
				align-items: center;

				.pic {
					width: 150rpx;
					height: 150rpx;
					border-radius: 10rpx;
				}

				.txt {
					margin-top: 12rpx;
					font-size: 28rpx;
					font-weight: 400;
					color: #BD9E81;
				}
			}
		}
	}

	.nav4.nav3 {

		.scroll-view {
			height: 356rpx;
		}

		.itemss {
			margin-top: 36rpx;
			display: flex;
			align-items: center;

			.item {
				margin-left: 24rpx;
				display: flex;
				flex-wrap: nowrap;
				align-items: center;

				.pic {
					height: 284rpx;
					width: 196rpx;
				}

				.right {
					width: 192rpx;
					margin-left: 20rpx;

					.txt1 {
						margin-bottom: 16rpx;
						font-size: 32rpx;
						font-weight: bold;
						color: #BD9E81;

						.small {
							margin-left: 12rpx;
							font-weight: 500;
							font-size: 24rpx;
						}
					}

					.txt2::before {
						content: '· ';
						position: absolute;
						left: -14rpx;
						top: 0;
						font-weight: 500;
					}

					.txt2 {
						position: relative;
						left: 14rpx;
						width: 192rpx;
						margin-top: 10rpx;
						font-size: 28rpx;
						font-weight: 500;
						color: #707071;
						word-wrap: break-word;
						word-break: break-all;
						white-space: pre-wrap;
					}

					.btn {
						margin-top: 24rpx;
						width: 186rpx;
						height: 52rpx;
						background: #FA8677;
						border-radius: 26rpx;
						display: flex;
						align-items: center;
						justify-content: center;

						.btn-img {
							width: 26rpx;
							height: 26rpx;
							margin-right: 6rpx;
						}

						.btn-txt {
							font-size: 28rpx;
							font-weight: 500;
							color: #FFFFFF;
						}
					}
				}
			}

		}

		.picc {
			width: 702rpx;
			height: 8rpx;
			margin-left: 26rpx;
			margin-bottom: 20rpx;
		}

		.picc2 {
			margin-left: 26rpx;
			width: 702rpx;
			height: 220rpx;
		}
	}
	.nav5{
		.swiper-item{
			background: #FFFFFF;
		}
		.nav5Items{
			padding: 8rpx 24rpx 20rpx 24rpx;
			background: #FFFFFF;
			display: flex;
			flex-wrap: wrap;
			justify-content: space-between;
			.item{
				margin-top: 24rpx;
				display: flex;
				flex-direction: column;
				align-items: center;
				box-sizing: border-box;
				width: 50%;
				.pic{
					width: 334rpx;
					height: 334rpx;
				}
				.txt{
					margin-top: 20rpx;
					width: 334rpx;
					font-size: 28rpx;
					font-weight: 500;
					color: #BD9E81;
				}
			}
		}
	}

</style>
