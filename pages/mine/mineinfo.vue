<template>
	<view class="mineinfo">
		<view class="mineinfo_form">
			<u--form
					labelPosition="left"
					:model="forminfo"
					ref="myform"
					>
						<u-form-item
							label="头像"
							prop="img"
							borderBottom
							ref="item1"
						>
							<u-upload
								name="6"
								multiple
								:maxCount="1"
								@afterRead="afterRead"
								width="250"
								height="150"
							>
								<view class="item_box">
									<view class="item_image">
										<u-avatar
												v-if="!forminfo.img"
												:text="forminfo.name.slice(forminfo.name.length-1)"
												fontSize="40rpx"
												randomBgColor
										></u-avatar>
										<image v-else :src="forminfo.img"></image>
									</view>
									<view class="item_icon">
										<van-icon name="arrow" color='#dddddd' size='40rpx'/>
									</view>
								</view>
							</u-upload>
					</u-form-item>
					<u-form-item
						label="姓名"
						prop="img"
						borderBottom
						ref="item1"
					>
					<view class="item_box">
						<u--input
								placeholder="未设置姓名"
								placeholderClass="name_ph"
								v-model="forminfo.name"
								border="none"
								disabled='false'
						></u--input>
					</view>
					</u-form-item>
					<u-form-item
						label="学号"
						prop="img"
						borderBottom
						ref="item1"
					>
					<view class="item_box">
						<u--input
								placeholder="未设置姓名"
								placeholderClass="name_ph"
								v-model="forminfo.Studentid"
								border="none"
								disabled='false'
						></u--input>
					</view>
					</u-form-item>
					<u-form-item
						label="昵称"
						prop="img"
						borderBottom
						ref="item1"
					>
					<view class="item_box">
						<u--input
								placeholder="未设置昵称"
								placeholderClass="name_ph"
								v-model="forminfo.nickname"
								border="none"
						></u--input>
						<view class="item_icon">
							<van-icon name="arrow" color='#dddddd' size='40rpx'/>
						</view>
					</view>
					</u-form-item>
					<u-form-item
						label="手机号"
						prop="img"
						borderBottom
						ref="item1"
					>
					<view class="item_box">
						<u--input
								placeholder="未设置电话号码"
								placeholderClass="name_ph"
								v-model="forminfo.phone"
								border="none"
								disabled='false'
						></u--input>
					</view>
					</u-form-item>
			</u--form>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				forminfo:{
					img:'',
					name:'杨展鹏',
					Studentid:'2018115020434',
					nickname:'杨展鹏',
					phone:'12345678910'
					
				},
			};
		},
		methods:{
			afterRead(event){
				console.log(event)
				this.forminfo.img=event.file[0].url
			}
		}
	}
</script>

<style lang="scss">
/deep/.mineinfo_form .u-form-item__body{
	display: flex !important;
	flex-direction: row !important;
	justify-content: space-between;
	align-items: center;
	padding:30rpx 20rpx;
}
/deep/.item_image .u-avatar--circle{
	position: relative;
	width: 60rpx !important;
	height: 60rpx !important;
}
/deep/.item_image .u-form-item__body__left{
	display: flex !important;
	flex-direction: row !important;
}
/deep/.item_image .u-text__value{
	position: absolute;
	left: 50%;
	top: 50%;
	transform: translate(-50%,-50%);
}
/deep/.item_box .u-input__content__field{
	display: block !important;
	text-align: end;
}
/deep/.item_box .u-input {
	background-color: #ffffff !important;
}
/deep/.mineinfo_form .u-form-item__body__left{
	width: 122rpx !important;
}
/deep/.mineinfo_form .u-upload{
	justify-content: flex-end;
}
.mineinfo{
	.mineinfo_form{
		.item_box{
			width: 100%;
			display: flex !important;
			flex-direction: row !important;
			align-items: center;
			justify-content: flex-end;
			.item_image{
				image{
					width: 60rpx;
					height: 60rpx;
					border-radius: 50%;
					
				}
			}
		}
	}
}
</style>
