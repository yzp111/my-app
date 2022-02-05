<template>
	<view class="info">
		<view class="info_header">
			<view class="header_name">我的月报</view>
			<view class="header_data">
				<view class="data_mon">{{info.data}}</view>
				<view class="data_time">{{info.time}}</view>
			</view>
		</view>
		<view class="info_today">
			<view class="today_title">
				本月工作
			</view>
			<view class="today_text">
				{{info.worktaday}}
			</view>
		</view>
		<view class="info_plan">
			<view class="plan_title">
				下月计划
			</view>
			<view class="plan_text">
				{{info.plan}}
			</view>
		</view>
		<view class="info_other">
			<view class="other_title">
				其他事项
			</view>
			<view class="other_text">
				{{info.other}}
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				info:{
					data:'1月21日',
					time:'18:57',
					name:'杨展鹏',
					worktaday:'哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈',
					plan:'哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈',
					other:'哈哈哈哈哈哈哈哈哈哈哈哈',
				},
			};
		},
		onReady() {
			console.log("mondate:",uni.getStorageSync('mondate'))
			console.log("montime:",uni.getStorageSync('montime'))
		}
	}
</script>

<style lang="scss">
page{
	width: 100%;
	height: 100%;
	background: #f5f7f6;
}
.info{
	.info_header{
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 24rpx;
		border-bottom: 1rpx solid #b7b7b7;
		.header_name{
			font-size: 36rpx;
			font-weight: 600;
			color: #000;
		}
		.header_data{
			display: flex;
			.data_mon{
				font-size: 26rpx;
				font-weight: 400;
				color: #989899;
			}
			.data_time{
				margin-left: 20rpx;
				font-size: 26rpx;
				font-weight: 400;
				color: #989899;
			}
		}
	}
	.info_today{
		margin-top: 30rpx;
		padding: 0 24rpx;
		.today_title{
			font-size: 36rpx;
			font-weight: 500;
			color: #989899;
			font-family: PingFangSC-Regular, PingFang SC;
		}
		.today_text{
			padding: 24rpx 0;
			font-size: 36rpx;
			font-weight: 500;
			color: #000000;
			font-family: PingFangSC-Regular, PingFang SC;
		}
	}
	.info_plan{
			margin-top: 30rpx;
			padding: 0 24rpx;
			.plan_title{
				font-size: 36rpx;
				font-weight: 500;
				color: #989899;
				font-family: PingFangSC-Regular, PingFang SC;
			}
			.plan_text{
				padding: 24rpx 0;
				font-size: 36rpx;
				font-weight: 500;
				color: #000000;
				font-family: PingFangSC-Regular, PingFang SC;
			}
	}
	.info_other{
			margin-top: 30rpx;
			padding: 0 24rpx;
			.other_title{
				font-size: 36rpx;
				font-weight: 500;
				color: #989899;
				font-family: PingFangSC-Regular, PingFang SC;
			}
			.other_text{
				padding: 24rpx 0;
				font-size: 36rpx;
				font-weight: 500;
				color: #000000;
				font-family: PingFangSC-Regular, PingFang SC;
			}
	}
}
</style>
