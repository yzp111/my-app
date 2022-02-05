<template>
	<view class="record">
		<view class="record_header">
			<van-tabs active="a" 
			color='#478de7' 
			line-width='200rpx' 
			swipeable='true'
			title-active-color='#478de7'>
				<van-tab title="我提交的" name="a">
					<view class="tabs_list" >
						<view class="list_item" v-for="(item,index) in Dailyinfo" :key='index'>
							<view class="item_title">{{item.date}}</view>
							<view class='item_box'>
								<view class="box_item" v-for="(it,i) in item.Dailydata" @click="goDailyinfo(item.date,it.time)">
									<view class="item_left">
										<view class="item_name">{{it.name}}</view>
										<view class="item_today">今日工作:{{it.worktaday}}</view>
										<view class="item_plan">明日计划:{{it.plan}}</view>
									</view>
									<view class="item_right">{{it.time}}</view>
								</view>
							</view>
						</view>
					</view>
				</van-tab>
			  <van-tab title="我收到的" name="b"></van-tab>
			</van-tabs>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				Dailyinfo:[
					{
						date:'1月21日',
						Dailydata:[
							{
								name:'杨展鹏',
								worktaday:'哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈',
								plan:'哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈',
								time:'18:51'
							
							},
							{
								name:'杨展鹏',
								worktaday:'哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈',
								plan:'哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈',
								time:'00:12'
							}
						]
					},
					{
						date:'1月19日',
						Dailydata:[
							{
								name:'杨展鹏',
								worktaday:'哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈',
								plan:'哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈',
								time:'18:57'
							}
						]
					}
				]
			};
		},
		methods:{
			goDailyinfo(date,time){
				try {
				    uni.setStorageSync('date', date);
					uni.setStorageSync('time', time);
					uni.navigateTo({
						url: '/pages/Daily/Dailyinfo'
					});
				} catch (e) {
					console.log(e)
				    console.log("error!!")
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
.record{
	.record_header{
		.tabs_list{
			.list_item{
				.item_title{
					font-size: 24rpx;
					font-weight: 500;
					color: #000000;
					margin:12rpx 0 12rpx 42rpx;
				}
				.item_box{
					margin: 0 auto;
					width: 702rpx;
					background: #FFFFFF;
					border-radius: 24rpx;
					.box_item{
						display: flex;
						flex-direction: row !important;
						justify-content: space-between;
						margin: 0 24rpx;
						padding: 24rpx 0;
						.item_left{
							width: 50%;
							flex: 5;
						}
						.item_name{
							font-size: 36rpx;
							font-weight: 600;
							color: #000;
						}
						.item_today{
							overflow: hidden;
							white-space: nowrap;
							text-overflow:ellipsis;//文本溢出显示省略号
							font-size: 28rpx;
							font-weight: 400;
							color:#989899;
						}
						.item_plan{
							overflow: hidden;
							white-space: nowrap;
							text-overflow: ellipsis;
							font-size: 28rpx;
							font-weight: 400;
							color:#989899;
						}
						.item_right{
							flex: 1;
							font-size: 24rpx;
							color: #989899;
							text-align: center;
						}
					}
				}
			}
		}
	}
}
</style>
