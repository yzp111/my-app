<template>
	<view class="record">
		<view class="record_header">
			<lx-calendar @change='change' ></lx-calendar>
		</view>
		<view class="record_box">
			<view class="box_header">
				<view class="header_left">
					<view class="header_title">上下班打卡</view>
					<view class="header_text">打卡规则</view>
				</view>
				<view class="header_right">
					<view class="right_icon">
						<van-icon name="arrow" size='40rpx' color='#b7b8ba'/>
					</view>
				</view>
			</view>
			<view class="box_content">
				<view class="content_scope">
					<view class="scope_mor" :class="ismortime?'active':''">
						{{mortime}}
					</view>
					<view class="scope_border"></view>
					<view class="scope_aft" :class="isafttime?'active':''">
						{{afttime}}
					</view>
				</view>
				<view class="content_info">
					<view class="info_mor">
						<view class="mor_title" :class="ismortime?'active':''">上午</view>
						<view v-if="ismortime" class="mortext">
							正常打卡({{clockmor}})
						</view>
					</view>
					<view class="info_aft">
						<view class="aft_title" :class="isafttime?'active':''">下午</view>
						<view v-if="isafttime" class="afttext">
							正常打卡({{clockaft}})
						</view>
					</view>
				</view>
			</view>
			<view class="record_longtime">
				<view class='longtime_title'>工作时长:</view>
				<view class='longtime_num'>{{isafttime&&ismortime?worktime:'-'}}</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	import lxCalendar from '../../components/lx-calendar/lx-calendar.vue'
	export default {
		components:{
		    lxCalendar,
		},
		data() {
			return {
				mortime:'09:00',
				afttime:'18:00',
				ismortime:true,
				isafttime:true,
				clockmor:'09:18',
				clockaft:'18:22',
				worktime:'',
			};
		},
		watch:{
			
		},
		onReady(){
			this.getlongtime()
		},
		methods:{
			change(e){
				console.log(e.fulldate)
			},
			getlongtime(){
				if(this.isafttime&&this.ismortime){
					let hour=Number(this.clockaft.slice(0,2))-Number(this.clockmor.slice(0,2))
					let min=0
					if(Number(this.clockaft.slice(3,5))<Number(this.clockmor.slice(3,5))){
						hour-=hour;
						 min=Number(this.clockaft.slice(3,5))+60-Number(this.clockmor.slice(3,5))
					}else{
						 min=Number(this.clockaft.slice(3,5))-Number(this.clockmor.slice(3,5))
					}
					if(min==0){
						this.worktime=hour+'小时'
					}else{
						this.worktime=hour+'小时'+min+'分钟'
					}
				}
			}
		}
	}
</script>

<style lang="scss">
page{
	width: 100%;
	height: 100%;
	background: #f5f7f6;
}
.record_box{
	margin: 0 auto;
	margin-top: 50rpx;
	width: 700rpx;
	background: #FFFFFF;
	border-radius: 24rpx;
	.box_header{
		padding: 24rpx 0;
		margin: 0 24rpx;
		display: flex !important;
		flex-direction: row !important;
		align-items: center;
		justify-content: space-between;
		border-bottom: 1rpx solid #b7b8ba;
		.header_left{
			.header_title{
				font-size: 32rpx;
				font-weight: 500;
				color: #000000;
				font-family: PingFangSC-Regular, PingFang SC;	
			}
			.header_text{
				margin-top: 12rpx;
				font-size: 26rpx;
				font-weight: 500;
				color: #b7b8ba;
				font-family: PingFangSC-Regular, PingFang SC;	
			}
		}
		.header_right{
			
		}
	}
	.box_content{
		display: flex !important;
		flex-direction: row !important;
		padding: 24rpx;
		.content_scope{
			font-size: 42rpx;
			font-weight: 600;
			color: #b7b8ba;
			font-family: PingFangSC-Regular, PingFang SC;
			display: flex !important;
			flex-direction: column !important;
			align-items: center;
			.active{
				color: #000000 !important;
			}
			.scope_border{
				width: 6rpx;
				height: 150rpx;
				background: #b7b8ba;
			}
		}
		.content_info{
			margin-left: 30rpx;
			display: flex !important;
			flex-direction: column !important;
			justify-content: space-between;
			.active{
				color: #000000 !important;
			}
			.info_mor{
				.mor_title{
					font-size: 42rpx;
					font-weight: 600;
					color: #b7b8ba;
					font-family: PingFangSC-Regular, PingFang SC;
				}
				.mortext{
					font-size: 32rpx;
					font-weight: 500;
					color: #b7b8ba;
					font-family: PingFangSC-Regular, PingFang SC;
				}
			}
			.info_aft{
				.aft_title{
					font-size: 42rpx;
					font-weight: 600;
					color: #b7b8ba;
					font-family: PingFangSC-Regular, PingFang SC;
				}
				.afttext{
					font-size: 32rpx;
					font-weight: 500;
					color: #b7b8ba;
					font-family: PingFangSC-Regular, PingFang SC;
				}
			}
		}
	}
	.record_longtime{
		padding: 24rpx;
		display: flex !important;
		flex-direction: row !important;
		align-items: center;
		.longtime_title{
			font-size: 32rpx;
			font-weight: 500;
			color: #000000;
			font-family: PingFangSC-Regular, PingFang SC;
		}
		.longtime_num{
			margin-left: 20rpx;
			font-size: 32rpx;
			font-weight: 500;
			color: #000000;
			font-family: PingFangSC-Regular, PingFang SC;
		}
	}
}
</style>
