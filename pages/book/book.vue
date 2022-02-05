<template>
<view class="book">
	
	<view class="book_mydepartment">
		<u-collapse
		  >
		    <u-collapse-item
		      title="我的组织"
		    >
			<view class="myteam" v-if="ismyteam">
				<view  class="mydepartment_box" @click="gobookteam">
					<view class="box_left">
						<image src="../../static/image/book/mydepartment_box_img.png"></image>
						<view class="box_text">工作室</view>
					</view>
					<view class="box_icon">
						<image src="../../static/image/book/mydepartment_box_icon.png"></image>
					</view>
				</view>
				<view  v-for="(item,index) in teaminfo" :key="index" class="mydepartment_team">
					<view class="box_left">
						<image :src="item.img"></image>
						<view class="box_text">{{item.name}}</view>
					</view>
					<view class="box_icon">
						<image src="../../static/image/book/mydepartment_box_icon.png"></image>
					</view>
			</view>
			</view>
		    </u-collapse-item>
		</u-collapse>
		<u-collapse
		  >
		    <u-collapse-item
		      title="最近联系人"
		    >
			<view class="book_contact">
					<view class="contact_list">
						<view class="list_item" v-for="(item,index) in contactlist" :key='index'>
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
			
		    </u-collapse-item>
		</u-collapse>
	</view>	
	</view>
</template>

<script>
	export default {
		data() {
			return {
				teaminfo:[
					{
						img:'../../static/image/book/mydepartment_box_img.png',
						name:'我的小组',
						flag:false,
					},
					{
						img:'../../static/image/book/mydepartment_box_img.png',
						name:'我的小组',
						flag:false,
					},
					{
						img:'../../static/image/book/mydepartment_box_img.png',
						name:'我的小组',
						flag:false,
					},
				],
				contactlist:[
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
				ismyteam:true,
			};
		},
		methods:{
			hendlePhone(val) {
			    uni.makePhoneCall({
			    		phoneNumber: val
			    	});
			},
			gobookteam(){
				try {
				    uni.setStorageSync('team', '');
					uni.navigateTo({
						url: '/pages/book/bookteam'
					});
				} catch (e) {
				    console.log("error!!")
				}
			},
			changemuteam(){
				this.ismyteam=!this.ismyteam
			}
		}
	}
</script>

<style lang="scss">
/deep/.book_mydepartment .u-cell__right-icon-wrap--up{
	display: none !important;
}
/deep/.book_mydepartment  .u-cell__right-icon-wrap--down{
	display: none !important;
}
/deep/.book_mydepartment .u-cell__body{
	padding: 20rpx !important;
}
/deep/.book_mydepartment .u-collapse-item__content__text {
	padding: 0 !important;
}
/deep/.list_item .u-avatar--circle{
	position: relative;
	width: 80rpx;
	height: 80rpx;
}
/deep/.list_item .u-text__value{
	position: absolute;
	left: 50%;
	top: 50%;
	transform: translate(-50%,-50%);
}
page{
	width: 100%;
	height: 100%;
	background: #f1f3f2;	
}
.book{
	.book_mydepartment{
		.mydepartment_title{
				display: flex !important;
				flex-direction: row !important;
				justify-content: space-between;
				padding: 20rpx 20rpx;
				font-size: 32rpx;
				font-family: PingFangSC-Regular, PingFang SC;
				font-weight: 400;
				color: #5e5e5e;
			}
		.myteam{
			.mydepartment_box{
							display: flex !important;
							flex-direction: row !important;
							justify-content: space-between;
							align-items: center;
							background: #FFF;
							padding:20rpx 20rpx;
							.box_left{
								display: flex !important;
								flex-direction: row !important;
								align-items: center;
								image{
									width: 80rpx;
									height: 80rpx;
								}
								.box_text{
									margin-left: 30rpx;
									font-size: 32rpx;
									font-family: PingFangSC-Regular, PingFang SC;
									font-weight: 600;
									color: #5e5e5e;
								}
							}
							.box_icon{
								display: flex !important;
								flex-direction: row !important;
								align-items: center;
								image{
									width: 60rpx;
									height: 60rpx;
								}
							}
					}
			.mydepartment_team{
						margin-top: 20rpx;
						display: flex !important;
						flex-direction: row !important;
						justify-content: space-between;
						align-items: center;
						background: #FFF;
						padding:20rpx 20rpx;
						.box_left{
							display: flex !important;
							flex-direction: row !important;
							align-items: center;
							image{
								width: 80rpx;
								height: 80rpx;
							}
							.box_text{
								margin-left: 30rpx;
								font-size: 32rpx;
								font-family: PingFangSC-Regular, PingFang SC;
								font-weight: 600;
								color: #5e5e5e;
							}
						}
						.box_icon{
							display: flex !important;
							flex-direction: row !important;
							align-items: center;
							image{
								width: 60rpx;
								height: 60rpx;
							}
						}
					}	
			}
		}
		.book_contact{
			.contact_list{
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
}
</style>
