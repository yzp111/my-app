<template>
	<view class="allapp">
		<view class="allapp_title">全部应用</view>
		<view class="allapp_list">
			<view class="list_item" v-for="(item,index) in allapp" :key="index">
				<image :src="item.img"></image>
				<view class="item_text">
					{{item.text}}
				</view>
			</view>	
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				allapp:[
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
					}, 
					{
						img:'../../static/image/app/application_offen_rb_icon.png',
						text:'日报',
						id:'6'
					},
					{
						img:'../../static/image/app/application_offen_qj_icon.png',
						text:'请假',
						id:'7'
					},
					{
						img:'../../static/image/app/application_offen_tm_icon.png',
						text:'竞赛',
						id:'8'
					},
					{
						img:'../../static/image/app/application_offen_rc_icon.png',
						text:'日常',
						id:'9'
					},
					{
						img:'../../static/image/app/application_offen_xz_icon.png',
						text:'我的小组',
						id:'9'
					}
				],
				type:'',
			};
		},
		onReady() {
			this.type = uni.getStorageSync('type');
			console.log(this.type)
		}
		
	}
</script>

<style lang="scss">
page{
		width: 100%;
		height: 100%;
		background: #f1f3f2;
}	
.allapp{
	.allapp_title{
		margin-top: 20rpx;
		display: block !important;
		width: 750rpx;
		padding: 20rpx 20rpx;
		font-size: 32rpx;
		font-family: PingFangSC-Regular, PingFang SC;
		font-weight: 400;
		color: #777777;
		background: #FFF;
	}
	.allapp_list{
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
</style>
