<template>
	<view class="mine">
		<view class="mine_info" @click="gomyinfo">
			<view class="mine_left">
				<view class="info_img">
					<u-avatar
							v-if="!mineinfo.img"
							:text="mineinfo.name.slice(mineinfo.name.length-1)"
							fontSize="60rpx"
							randomBgColor
					></u-avatar>
					<image v-else :src="mineinfo.img"></image>
				</view>
				<view class="info_right">
					<view class="right_nickname">{{!mineinfo.nickname?'还没设置昵称':'mineinfo.nickname'}}</view>
					<view class="right_info">
						<viwe class='right_name'>{{mineinfo.name}}</viwe>
						<view class="right_team">{{mineinfo.team}}</view>
					</view>
				</view>
			</view>
			<view class="mine_back">
				<van-icon name="arrow" size="50rpx" color='#989898'/>
			</view>
		</view>
		<view class="mine_list">
			<view class="list_item" v-for="(item,index) in minelist" :key='index' @click="goclickitem(item.id)">
				<view class="item_left">
					<view class="left_icon">
						<image :src="item.icon" mode=""></image>
					</view>
					<view class="left_text">
						{{item.text}}
					</view>
				</view>
				<view class="item-right">
					<van-icon name="arrow" size="50rpx" color='#989898'/>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				mineinfo:{
					img:'',
					nickname:'',
					name:'杨展鹏',
					team:'前端小组'
				},
				minelist:[
					{
						icon:'../../static/image/mine/mine_list_icon1.png',
						text:'打卡记录',
						id:'1',
					},
					{
						icon:'../../static/image/mine/mine_list_icon2.png',
						text:'日报记录',
						id:'2',
					},
					{
						icon:'../../static/image/mine/mine_list_icon3.png',
						text:'周报记录',
						id:'3',
					},
					{
						icon:'../../static/image/mine/mine_list_icon4.png',
						text:'月报记录',
						id:'4',
					},
					{
						icon:'../../static/image/mine/mine_list_icon5.png',
						text:'请假记录',
						id:'5',
					},
					{
						icon:'../../static/image/mine/mine_list_icon6.png',
						text:'我的评论',
						id:'6',
					}
					
				],
			}
		},
		methods: {
			gomyinfo(){
				uni.navigateTo({
					url: '/pages/mine/mineinfo'
				});
			},
			goclickitem(id){
				if(id==1){
					uni.navigateTo({
						url: '/pages/Clockin/clockinrecord'
					});
				}else if(id==2){
					uni.navigateTo({
						url: '/pages/Daily/Dailyrecord'
					});
				}else if(id==3){
					uni.navigateTo({
						url: '/pages/weekly/weeklyrecord'
					});
				}else if(id==4){
					uni.navigateTo({
						url: '/pages/monthly/monthlyrecord'
					});
				}else if(id==5){
					uni.navigateTo({
						url: '/pages/leave/leaverecord'
					});
				}
			},
			
		}
	}
</script>

<style lang="scss">
/deep/.info_img .u-avatar--circle{
	position: relative;
	width: 120rpx !important;
	height: 120rpx !important;
}
/deep/.info_img .u-text__value{
	position: absolute;
	left: 50%;
	top: 50%;
	transform: translate(-50%,-50%);
}
page{
	width: 100%;
	height: 100%;
	background: #f1f3f3;
}
.mine{
	.mine_info{
		margin-top: 20rpx;
		background: #FFF;
		display: flex !important;
		flex-direction: row !important;
		align-items: center;
		justify-content: space-between;
		padding: 20rpx;
		.mine_left{
			display: flex !important;
			flex-direction: row !important;
			align-items: center;
			.info_img{
				image{
					width: 120rpx;
					height: 120rpx;
				}
			}
			.info_right{
				margin-left: 10px;
				.right_nickname{
					font-size: 36rpx;
					font-weight: 500;
					color: #000000;
					font-family: PingFangSC-Regular, PingFang SC;
				}
				.right_info{
					display: flex !important;
					flex-direction: row !important;
					margin-top: 20rpx;
					.right_name{
						font-size: 28rpx;
						font-weight: 500;
						color: #000000;
						font-family: PingFangSC-Regular, PingFang SC;
					}
					.right_team{
						margin-left: 40rpx;
						font-size: 28rpx;
						font-weight: 500;
						color: #ababab;
						font-family: PingFangSC-Regular, PingFang SC;
					}
				}
			}
		}
	}
	.mine_list{
		margin-top: 20rpx;
		.list_item{
			border-bottom:6rpx solid #f1f3f3;
			padding:30rpx 20rpx;
			display: flex !important;
			flex-direction: row !important;
			justify-content: space-between;
			align-items: center;
			background: #FFFFFF;
			.item_left{
				display: flex !important;
				flex-direction: row !important;
				align-items: center;
				.left_icon{
					image{
						width: 42rpx;
						height: 42rpx;
					}
				}
				.left_text{
					margin-left: 32rpx;
					font-size: 32rpx;
					font-weight: 500;
					font-family: PingFangSC-Regular, PingFang SC;
					color: #2b2b2b;
				}
			}
		}
	}
}
</style>
