<template>
	<view class="login">
		<view class="login_header">
			<image src="../../static/image/login/login_header_img.png"></image>
		</view>
		<view class="login_form">
			<u--input
				    placeholder="请输入学号"
				    prefixIcon="account"
				    prefixIconStyle="font-size: 50rpx;color: #ff8927"
					v-model="info.studentid"
				></u--input>
				<u--input
				    placeholder="请输入密码"
				    prefixIcon="lock"
				    prefixIconStyle="font-size: 50rpx;color: #ff8927"
					type='password'
					v-model="info.password"
				></u--input>
		</view>
		<view class="login_btn">
			<button class="btn_login" @click="gologin">登录 </button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				info:{
					studentid:'',
					password:'',
				}
			};
		},
		methods:{
			gologin(){
				uni.switchTab({
				    url: "../home/index",
			})
			}
		}
	}
</script>

<style lang="scss">
/deep/.login_form .u-input{
	margin: 32rpx 32rpx !important;
}
/deep/.login_form .u-input__content{
	display: flex !important;
}
/deep/.login_form .u-border{
	border: 0 !important;
	border-bottom: 1rpx solid #ff8927 !important;
}
.login{
	.login_header{
		image{
			width: 100%;
			height: 400rpx;
		}
	}
	.login_btn{
		padding: 0;
		margin: 0 auto;
		margin-top: 100rpx;
		width: 500rpx;
		height: 100rpx;
		background: #ff8927 ;
		button{
			width: 100%;
			height: 100%;
			background-color: #ff8927;
			font-size: 42rpx;
			color: #FFFFFF;
			line-height: 100rpx;
		}
	}
}
</style>
