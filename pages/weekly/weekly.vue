<template>
	<view class="Daily">
		<view class="Daily_toady">
			<view class="today_title">本周工作</view>
			<u--textarea v-model="todatdata" placeholder="请输入" ></u--textarea>
		</view>
		<view class="Daily_mortime">
			<view class="today_title">下周计划</view>
			<u--textarea v-model="mordata" placeholder="请输入" ></u--textarea>
		</view>
		<view class="Daily_other">
			<view class="today_title">其他事项</view>
			<u--textarea v-model="otherdata" 
			placeholder="请输入"
			></u--textarea>
		</view>
		<view class="Daily_confirm">
			<view class='confirm_btn'>提交</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				todatdata:'',
				mordata:'',
				otherdata:'',
			};
		}
	}
</script>

<style lang="scss">
/deep/.Daily_toady .u-border{
	border: 0 !important;
}
/deep/.Daily_toady .u-textarea__field{
	width: 100% !important;
	height:300rpx !important;
	font-size: 36rpx;
	font-weight: 500;
	font-family: PingFangSC-Regular, PingFang SC;
	
}
/deep/.Daily_toady .u-textarea{
	padding:0 24rpx;
}
/deep/.Daily_mortime .u-border{
	border: 0 !important;
}
/deep/.Daily_mortime .u-textarea__field{
	width: 100% !important;
	height:300rpx !important;
	font-size: 36rpx;
	font-weight: 500;
	font-family: PingFangSC-Regular, PingFang SC;
	
}
/deep/.Daily_mortime .u-textarea{
	padding:0 24rpx;
}
/deep/.Daily_other .u-border{
	border: 0 !important;
}
/deep/.Daily_other .u-textarea__field{
	width: 100% !important;
	height:300rpx !important;
	font-size: 36rpx;
	font-weight: 500;
	font-family: PingFangSC-Regular, PingFang SC;
	
}
/deep/.Daily_other .u-textarea{
	padding:0 24rpx;
}
page{
	width: 100%;
	height: 100%;
	background: #f5f7f6;	
}
.Daily{
	.Daily_toady{
		width: 100%;
		background: #FFFFFF;
		margin-top: 30rpx;
		.today_title{
			padding:12rpx 24rpx;
			font-size: 36rpx;
			font-weight: 500;
			font-family: PingFangSC-Regular, PingFang SC;
		}
	}
	.Daily_mortime{
		width: 100%;
		background: #FFFFFF;
		margin-top: 30rpx;
		.today_title{
			padding:12rpx 24rpx;
			font-size: 36rpx;
			font-weight: 500;
			font-family: PingFangSC-Regular, PingFang SC;
		}
	}
	.Daily_other{
		width: 100%;
		background: #FFFFFF;
		margin-top: 30rpx;
		.today_title{
			padding:12rpx 24rpx;
			font-size: 36rpx;
			font-weight: 500;
			font-family: PingFangSC-Regular, PingFang SC;
		}
	}
	.Daily_confirm{
		margin: 0 auto;
		margin-top: 30rpx;
		width: 700rpx;
		height: 100rpx;
		.confirm_btn{
			width: 100%;
			height: 100%;
			background: #257fef;
			text-align: center;
			line-height: 100rpx;
			color: #FFFFFF;
			font-size: 32rpx;
			font-weight: 500;
		}
	}
}
</style>
