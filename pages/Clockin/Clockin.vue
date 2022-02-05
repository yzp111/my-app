<template>
	<view class="Clockin">
		<view class="Clockin_map">
			<map 
			@click="getLocation"
			:latitude="latitude"
			:longitude="longitude"></map>	
		</view>
		<view class="Clockin_tips" :class="!isscope?'Clockin_noscope':''">
			{{isscope?'您已在打卡范围':'您不在打卡范围'}}
		</view>
		<view class="Clockin_btn" @click="changeclockin">
			{{isclcok?'已打卡':clocktext}}
		</view>
		<view class="Clockin_pop" v-if="isshow">
			<view class="pop_content">
				<view class="pop_icon">
					<van-icon name="warning" size='100rpx' color='#e67374'/>
				</view>
				<view class="pop_text">
					未在打卡时间
				</view>
				<view class="pop_btn" @click="popclose">确定</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				isclcok:false,
				longitude:'',
				latitude:'',
				isscope:true,
				istime:true,
				clocktext:'打卡',
				isshow:false
			};
		},
		methods:{
			getLocation() {
			  // 使用Promise包装uni.getLocation, 增加可读性（有回调函数的方法都可以这样做）
			  new Promise((resolve, rejected) => {
				//这里采用的是微信小程序封装的api getLocation，来获取用户的当前地理位置
				uni.getLocation({
				  type: 'gcj02',
				  timeout: '2000',
				  success: res => resolve(res),
				  fail: err => rejected(err)
				})
			  }).then(res => {
				  console.log(res)
				//假如初次没有使用show-Location属性便可以使用这种方法来赋予地图经纬度的初始位置
				this.longitude = res.longitude
				this.latitude = res.latitude
			  }).catch(err => {
				//错误处理
				uni.showToast({
				  title: '位置信息获取失败（请检查定位功能是否打开）',
				  icon:'none',
				})
			  })
			},
			changeclockin(){
				if(!this.isclcok){
					if(this.istime){
						this.getLocation()
						this.clocktext='打卡成功'
					}else{
						this.isshow=true
					}
				}
			},
			popclose(){
				this.isshow=!this.isshow
			}
		   },
		   onReady() {
				console.log(123)
				this.getLocation() 
		   },
	}
</script>

<style lang="scss">
	.Clockin{
		.Clockin_map{
			margin-top: 120rpx;
			display: flex !important;
			justify-content: center;
		}
		.Clockin_tips{
			margin-top: 50rpx;
			font-size: 42rpx;
			color:#6eb327 ;
			text-align: center;
		}
		.Clockin_noscope{
			color: #e67374;
		}
		.Clockin_btn{
			margin: 0 auto;
			margin-top: 150rpx;
			border: 10rpx solid #6eb327;
			width: 200rpx;
			height: 200rpx;
			font-size: 50rpx;
			color: #000000;
			border-radius: 50%;
			line-height: 200rpx;
			text-align: center;
		}
		.Clockin_pop{
			width: 100%;
			height: 100%;
			position: fixed;
			top: 0;
			left: 0;
			background: rgba(#000000, 0.5);
			text-align: center;
			.pop_content{
				border-radius: 24rpx;
				width: 350rpx;
				background: #FFFFFF;
				position: fixed;
				top: 50%;
				left: 50%;
				transform: translate(-50%,-50%);
				.pop_icon{
					margin-top: 50rpx;
				}
				.pop_text{
					margin-top: 30rpx;
					font-size: 36rpx;
					font-weight: 500;
					color: #000000;
					font-family: PingFangSC-Regular, PingFang SC;
				}
				.pop_btn{
					margin: 0 auto;
					border-radius: 14rpx;
					width: 140rpx;
					height: 50rpx;
					background: #257fe9;
					margin-top: 30rpx;
					font-size: 24rpx;
					font-weight: 500;
					color: #FFFFFF;
					font-family: PingFangSC-Regular, PingFang SC;
					line-height: 50rpx;
					margin-bottom: 50rpx;
				}
			}
		}
	}

</style>
