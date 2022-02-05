<template>
	<view class="application">
		<view class="application_swiper">
			<u-swiper :list="imgs"
			  indicator
			  indicatorMode="line"
			  circular   
			></u-swiper>
		</view>
		<view class="application_offen">
			<view class="offen_title">常用服务</view>
			<view class="offen_box">
				<view class="offen_left" @click="goClockin">
					<image src="../../static/image/app/application_offen_dk_icon.png" alt="">
					<view class="left_text">打卡</view>
				</view>
				<view class="offen_right">
					<view class="right_item" v-for="(item,index) in offeritem" :key='index' @click="clickitem(item.type)" >
						<image :src="item.img" alt="">
						<view class="right_text">{{item.text}}</view>
					</view>
				</view>
			</view>
		</view>
		<view class="application_more">
			<viwe class="more_title">其他服务</viwe>
			<view class="more_list">
				<view class="list_item" v-for="(item,index) in moreitem" :key="index" @click="goclick(item.id)" >
					<image :src="item.img"></image>
					<view class="item_text">
						{{item.text}}
					</view>
				</view>
				<view class="list_item" @click="handleadd">
					<image src="../../static/image/app/application_more_add_icon.png"></image>
					<view class="item_text">
						添加
					</view>
				</view>
				<view class="list_item"  @click="handleall">
					<image src="../../static/image/app/application_more_all_icon.png"></image>
					<view class="item_text">
						全部
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
				imgs:[
					'https://ns-strategy.cdn.bcebos.com/ns-strategy/upload/fc_big_pic/part-00262-3296.jpg',
					'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Finews.gtimg.com%2Fnewsapp_match%2F0%2F11246944353%2F0.jpg&refer=http%3A%2F%2Finews.gtimg.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1644487066&t=02fbe6c94a2ef480a8542261deca4b7a',
					'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fcontent.pic.tianqistatic.com%2Fcontent%2Fjierizixun%2Fshouchaobao%2Fimages%2F202001%2F16%2Fe427cb3fe73ec712.jpg%2Fwnl_pc&refer=http%3A%2F%2Fcontent.pic.tianqistatic.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1644487066&t=6c6af38efe964d5bae2de314eae9db4b',
				],
				offeritem:[
					{
						img:'../../static/image/app/application_offen_rb_icon.png',
						text:'日报',
						type:'Daily'
					},
					{
						img:'../../static/image/app/application_offen_qj_icon.png',
						text:'请假',
						type:'leave'
					},
					{
						img:'../../static/image/app/application_offen_tm_icon.png',
						text:'竞赛'
					},
					{
						img:'../../static/image/app/application_offen_rc_icon.png',
						text:'日常'
					},
				],
				moreitem:[
					{
						img:'../../static/image/app/application_more_zb_icon.png',
						text:'周报',
						id:'1'
					},
					{
						img:'../../static/image/app/application_more_tz_icon.png',
						text:'通知',
						id:'2'
					},
					{
						img:'../../static/image/app/application_more_yb_icon.png',
						text:'月报',
						id:'3'
					}
				],
			}
		},
		methods:{
			handleadd(){
				try {
				    uni.setStorageSync('type', 'add');
					uni.navigateTo({
						url: '/pages/application/allapp'
					});
				} catch (e) {
				    console.log("error!!")
				}
			},
			handleall(){
				try {
				    uni.setStorageSync('type', 'all');
					uni.navigateTo({
						url: '/pages/application/allapp'
					});
				} catch (e) {
				    console.log("error!!")
				}
			},
			goClockin(){
				uni.navigateTo({
					url: '/pages/Clockin/Clockin'
				});
			},
			clickitem(type){
				if(type=='Daily'){
					uni.navigateTo({
						url: '/pages/Daily/Daily'
					});
				}
				if(type=='leave'){
					uni.navigateTo({
						url: '/pages/leave/leave'
					});
				}
			},
			goclick(id){
				if(id==3){
					uni.navigateTo({
						url: '/pages/monthly/monthly'
					})
				}
				if(id==1){
					uni.navigateTo({
						url: '/pages/weekly/weekly'
					})
				}
			}
			}
	}
</script>

<style lang="scss">
/deep/.application_swiper .u-swiper{
	height: 300rpx !important;
}
/deep/.application_swiper .u-swiper__wrapper{
	height: 300rpx !important;
}

/deep/.application_swiper .u-swiper{
	position: relative;
}
/deep/.application_swiper .u-swiper-indicator__wrapper--line{
	width: 132rpx !important;
}
/deep/.application_swiper .u-swiper-indicator__wrapper--line__bar{
	width: 44rpx !important;
}
/deep/.application_swiper .u-swiper__indicator {
	left: 50%;
	transform: translate(-50%);
}
/deep/.application_swiper .u-swiper__wrapper__item__wrapper__image{
	height: 300rpx !important;
	width: 100%;
}
page{
	width: 100%;
	height: 100%;
	background: #f1f3f2;
}
.application{
	.application_offen{
		margin-top: 20rpx;
		width: 100%;
		background: #FFF;
		.offen_title{
			padding: 20rpx 20rpx;
			font-size: 32rpx;
			font-family: PingFangSC-Regular, PingFang SC;
			font-weight: 400;
			color: #5e5e5e;
		}
		.offen_box{
			display: flex !important;
			flex-direction: row !important;
			justify-content: space-between;
			align-items: center;
			border:1px solid #fafafa;
			.offen_left{
				width: 34%;
				display: flex !important;
				flex-direction: column !important;
				align-items: center;
				text-align: justify;
					image{
						width: 100rpx;
						height: 100rpx;
					}
					.left_text{
						font-size: 28rpx;
						font-family: PingFangSC-Regular, PingFang SC;
						font-weight: 400;
						color: #5e5e5e;
					}
				}
			.offen_right{
					width: 66%;
					display: flex !important;
					flex-direction: row !important;
					flex-wrap: wrap;
					.right_item{
						width: 49%;
						display: flex !important;
						flex-direction: row !important;
						padding: 50rpx 0;
						justify-content: center;
						border:1px solid #fafafa;
						border-bottom: 0px;
						image{
							width: 42rpx;
							height: 42rpx;
						}
						.right_text{
							margin-left: 6rpx;
							font-size: 28rpx;
							font-family: PingFangSC-Regular, PingFang SC;
							font-weight: 400;
							color: #6f6f6f;
						}
					}
				
				}
			
		}
	}
	.application_more{
		margin-top: 20rpx;
		.more_title{
			display: block !important;
			width: 750rpx;
			padding: 20rpx 20rpx;
			font-size: 32rpx;
			font-family: PingFangSC-Regular, PingFang SC;
			font-weight: 400;
			color: #777777;
			background: #FFF;
		}
		.more_list{
			display: flex !important;
			flex-direction: row !important;
			flex-wrap: wrap;
			.list_item{
				width: calc(20% - 4rpx);
				display: flex !important;
				flex-direction: column !important;
				align-items: center;
				padding: 39rpx 0;
				border:1rpx solid #fafafa;
				background: #FFF;
				image{
					width: 42rpx;
					height: 42rpx;
				}
				.item_text{
					margin-top: 8rpx;
					font-size: 28rpx;
					font-family: PingFangSC-Regular, PingFang SC;
					font-weight: 400;
					color: #5e5e5e;
				}
			}
		}
	}
}
	
</style>
