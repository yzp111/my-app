<template>
	<view class="bookteam">
		<view class="header">
			<view class="bookteam_header">
				<view class="header_back" @click="goback">
					<van-icon name="arrow-left" size="42rpx" />
				</view>
				<view class="header_title">
					工作室
				</view>
				<view></view>
			</view>
			<view class="bookteam_content">
				<view class="content_search">
					<view class="header_input">
						<view class="input_box">
							<image src="../../static/image/home/home_header_input_icon.png"></image>
							<text>请输入关键字进行搜索</text>
						</view>
					</view>
				</view>
		</view>
		</view>
		<view class="bookteam_list">
			<view class="contact_list">
					<view class="list_item" v-for="(item,index) in teamlist" :key='index'>
						<view class="item_left">
							<view class="left_img">
								    <u-avatar
											v-if="!item.img"
								            :text="item.name.slice(item.name.length-1)"
								            fontSize="50rpx"
								            randomBgColor
								    ></u-avatar>
									<view v-else class="img">
										<image :src="item.img"></image>
									</view>
									<view class="img_name">{{item.name}}</view>
									<view class="img_grade">({{item.grade}})</view>
							</view>
							<view class="left_info">
								<view class="info_phone">{{item.phone}}</view>
								<view class="info_team">{{item.team}}</view>
								<view class="info_teacher">老师：{{item.teacher}}</view>
								<view class="info_post">职位：{{item.post}}</view>
							</view>
						</view>
						<view class="item_right">
							<view class="right_phone" @click="hendlePhone(item.phone)">
								<image src="../../static/image/book/contact_list_phone.png"></image>
							</view>
							<view class="right_chat">
								<image src="../../static/image/book/contact_list_chat.png"></image>
							</view>
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
				teamlist:[
						{
							img:'',
							name:'杨展鹏',
							grade:'2018',
							phone:'12345678910',
							team:'前端小组',
							teacher:'杨展鹏',
							post:'成员'
						},
						{
							img:'',
							name:'杨展鹏',
							grade:'2018',
							phone:'12345678910',
							team:'前端小组',
							teacher:'杨展鹏',
							post:'成员'
						},
						{
							img:'',
							name:'杨展鹏',
							grade:'2018',
							phone:'12345678910',
							team:'前端小组',
							teacher:'杨展鹏',
							post:'成员'
						},
						{
							img:'',
							name:'杨展鹏',
							grade:'2018',
							phone:'12345678910',
							team:'前端小组',
							teacher:'杨展鹏',
							post:'成员'
						},
						{
							img:'',
							name:'杨展鹏',
							grade:'2018',
							phone:'12345678910',
							team:'前端小组',
							teacher:'杨展鹏',
							post:'成员'
						},
						{
							img:'',
							name:'杨展鹏',
							grade:'2018',
							phone:'12345678910',
							team:'前端小组',
							teacher:'杨展鹏',
							post:'成员'
						},
						{
							img:'',
							name:'杨展鹏',
							grade:'2018',
							phone:'12345678910',
							team:'前端小组',
							teacher:'杨展鹏',
							post:'成员'
						},
						{
							img:'',
							name:'杨展鹏',
							grade:'2018',
							phone:'12345678910',
							team:'前端小组',
							teacher:'杨展鹏',
							post:'成员'
						},
					],
				
			};
		},
		methods:{
			goback(){
				uni.navigateBack()
			},
			hendlePhone(val) {
			    uni.makePhoneCall({
			    		phoneNumber: val
			    	});
			},
		}
		
	}
</script>

<style lang="scss">
page{
	background: #f1f3f2;	
}	
.bookteam{
	.header{
		width: 100%;
		position: fixed;
		top: 0;
		left: 0;
		.bookteam_header{
				padding:100rpx 20rpx 20rpx 20rpx;
				display: flex !important;
				flex-direction: row !important;
				justify-content: space-between;
				align-items: center;
				background: #FFF;
				.header_title{
					text-align: center;
				}
			}
		.bookteam_content{
				padding:0 20rpx;
				.content_search{
					margin-top:16rpx;
					width:100%;
					.input_box{
						display: flex !important;
						flex-direction: row !important;
						align-items: center;
						justify-content: center;
						width: 100%;
						padding: 16rpx 0;
						background: #FFFFFF;
						border-radius:12rpx;
						image{
							width: 32rpx;
							height: 32rpx;
							color: #cdcdcd;
						}
						text{
							font-size: 24rpx;
							color: #cdcdcd;
						}
					}
				}
			}
		
	}
	}
	.bookteam_list{
		margin-top: 258rpx;
		.contact_list{
			overflow-y: scroll;
			max-height: calc(100vh - 350rpx);
				.list_item{
					background: #FFF;
					padding: 20rpx 20rpx;
					border-bottom: 1px solid #fafafa ;
					display: flex !important;
					flex-direction: row !important;
					justify-content: space-between;
					.item_left{
						display: flex !important;
						flex-direction: row !important;
						align-items: center;
						.left_img{
							display: flex !important;
							flex-direction: column !important;
							align-items: center;
							.img{
								width: 80rpx;
								height: 80rpx;
								image{
									border-radius: 50%;
									width: 80rpx;
									height: 80rpx;
								}
							}
							.img_name{
								font-size: 32rpx;
								font-family: PingFangSC-Regular, PingFang SC;
								font-weight: 600;
								color: #5e5e5e;
								line-height: 48rpx;
							}
							.img_grade{
								font-size: 32rpx;
								font-family: PingFangSC-Regular, PingFang SC;
								font-weight: 400;
								color: #5e5e5e;
							}
						}
						.left_info{
							margin-left: 30rpx;
							font-size: 32rpx;
							font-family: PingFangSC-Regular, PingFang SC;
							font-weight: 400;
							color: #8a8a8a;
							.info_phone{
								line-height: 48rpx;
							}
							.info_team{
								line-height: 48rpx;
							}
							.info_teacher{
								line-height: 48rpx;
							}
							.info_post{
								line-height: 48rpx;
							}
						}
					}
					.item_right{
						display: flex !important;
						flex-direction: row !important;
						.right_phone{
							image{
								width: 42rpx;
								height: 42rpx;
		
							}
						}
						.right_chat{
							margin-left: 32rpx;
							image{
								width: 48rpx;
								height: 42rpx;
							}
						}
					}
				}
			}
		
	}
</style>
