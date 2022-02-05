<template>
	<view class="leave">
		<view class="leave_form">
			<view class="form_start">
				<view class="start_box" @click="changestart">
					<view class="start_icon">
						<image src="../../static/image/leave/start_time_img.png" mode=""></image>
						<view class="start_title">开始时间</view>
					</view>
					<view class="start_time">
						<view class="time_text">{{starttime}}</view>
						<view class="time_icon">
							<van-icon name="arrow" color="#adadad" size="50rpx" />
						</view>
					</view>
				</view>
			</view>
			<view class="form_end">
				<view class="end_box" @click="changeend">
					<view class="end_icon">
						<image src="../../static/image/leave/start_time_img.png" mode=""></image>
						<view class="end_title">结束时间</view>
					</view>
					<view class="end_time">
						<view class="end_text">{{endtime}}</view>
						<view class="end_icon">
							<van-icon name="arrow" color="#adadad" size="50rpx" />
						</view>
					</view>
				</view>
			</view>
			<view class="form_daynum">
				<view class="day_box">
					<view class="day_icon">
						<image src="../../static/image/leave/start_day_img.png" mode=""></image>
						<view class="day_title">请假天数</view>
					</view>
					<view class="day_time">
						<view class="day_text">{{daynum}}</view>
					</view>
				</view>
			</view>
			<view class="form_reason">
				<van-cell-group>
				  <van-field
				  label="请假原因"
				    :value="value"
				    placeholder="请输入请假原因"
				    border="false"
				    @change="onChange"
				  />
				</van-cell-group>
			</view>
		</view>
		<view class="leave_btn">
			<view class="btn_confim">提交</view>
		</view>
		<van-notify id="van-notify" />
		<van-popup
		 :show="isstarttime"
		 position="bottom"
		 @close="onClose1"
		 >
			<van-datetime-picker
			  type="date"
			  :value="currentdate"
			  :formatter="formatter"
			  @cancel="oncancel1"
			  @confirm="onInput1"
			  :min-date="minDate"
			  :max-date="maxDate"
			/>
		</van-popup>
		<van-popup
		 :show="isendtime"
		 position="bottom"
		 @close="onClose2"
		 >
			<van-datetime-picker
			  type="date"
			  :value="currentdate"
			  :formatter="formatter"
			  @cancel="oncancel2"
			  @confirm="onInput2"
			  :min-date="minDate"
			  :max-date="maxDate"
			/>
		</van-popup>
	</view>
</template>

<script>
	import Notify from '../../wxcomponents/vant/notify/notify.js'
	export default {
		data() {
			return {
				starttime:'',
				endtime:'',
				daynum:'1',
				reason:'',
				isstarttime:false,
				isendtime:false,
				currentdate: new Date().getTime(),
				minDate: new Date().getTime(),
				maxDate: new Date().getTime()+(3600*24*365*1000),
				formatter(type, value) {
				    if (type === 'year') {
						return `${value}年`;
				    }
				    if (type === 'month') {
				        return `${value}月`;
				    }
				    return value;
				    },
			};
		},
		onReady(){
			this.gettimestart(new Date().getTime())
			this.gettimeend(new Date().getTime())
			this.getday()
		},
		methods:{
			 onChange(event) {
				 this.reason=event.detail
			    // event.detail 为当前输入的值
			    console.log(this.reason);
			  },
			 onInput1(event) {
				this. gettimestart(event.detail)
				 this.isstarttime=false
				  this.getday()
			  },
			  gettimestart(t){
				  let time=new Date(parseInt(t)).toLocaleString()
				  for(let i=0;i<time.length;i++){
				  	if(time[i]===' '){
				  		this.starttime=time.slice(0,i)
				  	}
				  }
			  },
			  onInput2(event){
				 this.gettimeend(event.detail)
				 this.isendtime=false
				 this.getday()
			  },
			  gettimeend(t){
			  		let time=new Date(parseInt(t)).toLocaleString()
			  		for(let i=0;i<time.length;i++){
			  			if(time[i]===' '){
			  			this.endtime=time.slice(0,i)
			  		}
			  	}
			  },
			  changestart(){
				  this.isstarttime=!this.isstarttime
			  },
			  changeend(){
					this.isendtime=!this.isendtime
			  },
			  oncancel1(){
				   this.isstarttime=false
			  },
			  oncancel2(){
			  		this.isendtime=false
			  },
			  onClose1(){
				   this.isstarttime=false
			  },
			  onClose2(){
			  		this.isendtime=false
			  },
			  getday(){
				let startt=this.starttime.split('/').join('-')
				let endt=this.endtime.split('/').join('-')
				let day1 = new Date(startt);
				let day2 = new Date(endt);
				let num=(day2 - day1) / (1000 * 60 * 60 * 24)+1
				if(num>=1){
					this.daynum=num
				}else{
					// 警告通知
					Notify({ type: 'warning', message: '日期开始时间不能小于结束时间' });
				}
				
			  }
		}
	}
</script>

<style lang="scss">
/deep/.form_reason .van-field__label{
	font-size: 36rpx;
	font-family: PingFangSC-Regular, PingFang SC;
	font-weight: 500;
	color: #000;
}
	page{
		width: 100%;
		height: 100%;
		background: #f2f2f2;
	}
.leave{
	.leave_form{
		.form_start{
			margin-top: 12rpx;
			background: #FFFFFF;
			.start_box{
				display: flex;
				flex-direction: row !important;
				justify-content: space-between;
				align-items: center;
				padding: 12rpx 0;
				border-bottom: 1rpx solid #efefef;
				margin:0 24rpx;
			}
			.start_icon{
				display: flex;
				flex-direction: row !important;
				align-items: center;
				image{
					width: 60rpx;
					height: 60rpx;
				}
				.start_title{
					margin-left: 16rpx;
					font-size: 36rpx;
					font-family: PingFangSC-Regular, PingFang SC;
					font-weight: 500;
					color: #000;
				}
			}
			.start_time{
				display: flex;
				flex-direction: row !important;
				align-items: center;
				.time_text{
					font-size: 32rpx;
					font-family: PingFangSC-Regular, PingFang SC;
					font-weight: 500;
					color: #adadad;
				}
			}
		}
		.form_end{
				background: #FFFFFF;
				.end_box{
					display: flex;
					flex-direction: row !important;
					justify-content: space-between;
					align-items: center;
					padding: 12rpx 0;
					border-bottom: 1rpx solid #efefef;
					margin:0 24rpx;
				}
				.end_icon{
					display: flex;
					flex-direction: row !important;
					align-items: center;
					image{
						width: 60rpx;
						height: 60rpx;
					}
					.end_title{
						margin-left: 16rpx;
						font-size: 36rpx;
						font-family: PingFangSC-Regular, PingFang SC;
						font-weight: 500;
						color: #000;
					}
				}
				.end_time{
					display: flex;
					flex-direction: row !important;
					align-items: center;
					.end_text{
						font-size: 32rpx;
						font-family: PingFangSC-Regular, PingFang SC;
						font-weight: 500;
						color: #adadad;
					}
				}
			}
		
	}
		.form_daynum{
			margin-top: 20rpx;
			background: #FFFFFF;
			.day_box{
				display: flex;
				flex-direction: row !important;
				justify-content: space-between;
				align-items: center;
				padding: 12rpx 0;
				border-bottom: 1rpx solid #efefef;
				margin:0 24rpx;
			}
			.day_icon{
				display: flex;
				flex-direction: row !important;
				align-items: center;
				image{
					width: 60rpx;
					height: 60rpx;
				}
				.day_title{
					margin-left: 16rpx;
					font-size: 36rpx;
					font-family: PingFangSC-Regular, PingFang SC;
					font-weight: 500;
					color: #000;
				}
			}
			.day_time{
				display: flex;
				flex-direction: row !important;
				align-items: center;
				.day_text{
					font-size: 36rpx;
					font-family: PingFangSC-Regular, PingFang SC;
					font-weight: 500;
					color: #000000;
					padding-right: 40rpx;
				}
			}
	}
		.form_reason{
			margin-top: 80rpx;
		}
     }
    .leave_btn{
		margin: 0 auto;
		width: 500rpx;
		height: 100rpx;
		margin-top: 400rpx;
		.btn_confim{
			width: 100%;
			height: 100%;
			background: #ff8927;
			font-size: 36rpx;
			font-family: PingFangSC-Regular, PingFang SC;
			font-weight: 500;
			color: #FFFFFF;
			text-align: center;
			line-height: 100rpx;
			border-radius: 24rpx;
		}
	}
</style>
