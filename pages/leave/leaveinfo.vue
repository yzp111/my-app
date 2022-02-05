<template>
	<view class="info">
		<view class="info_header">
			<view class="header_name">我的日报</view>
			<view class="header_data">
				<view class="data_mon">{{info.data}}</view>
				<view class="data_time">{{info.time}}</view>
			</view>
		</view>
		<view class="info_today">
			<view class="today_title">
				开始时间
			</view>
			<view class="today_text">
				{{info.starttime}}
			</view>
		</view>
		<view class="info_plan">
			<view class="plan_title">
				结束时间
			</view>
			<view class="plan_text">
				{{info.endstart}}
			</view>
		</view>
		<view class="info_other">
			<view class="other_title">
				请假原因
			</view>
			<view class="other_text">
				{{info.reason}}
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
					starttime:'123',
					endstart:'123',
					reason:'哈哈哈哈哈哈哈哈哈哈哈哈',
				},
			};
		},
		onReady() {
			console.log("leavedate:",uni.getStorageSync('date'))
			console.log("leavetime:",uni.getStorageSync('time'))
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
