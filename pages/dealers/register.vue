<template>
	<view class="register">
		<view class="register_form">
			<u--form 
				labelPosition="left"
				:model="forminfo"
				ref='myform'
			> 
				<u-form-item
							required='true'
							label="姓名"
							prop="name"
							borderBottom
							ref="item1"
				>
						<u--input
								placeholderStyle="color: #93969D"
								placeholder="请输入姓名"
								v-model="forminfo.name"
								border="none"
						></u--input>
				</u-form-item>
				<u-form-item
							required='true'
							label="性别"
							prop="sex"
							borderBottom
							ref="item1"
							>
							 <u-radio-group
							    v-model="forminfo.sex"
							    placement="row"
							  >
							    <u-radio
							      v-for="(item, index) in sex"
							      :key="index"
							      :label="item"
							      :name="item"
								  @change="radioChange"
							    >
							    </u-radio>
							  </u-radio-group>
				</u-form-item>
				<u-form-item
							required='true'
							label="身份证号"
							prop="identity"
							borderBottom
							ref="item1"
							>
							<u--input
									placeholderStyle="color: #93969D"
									placeholder="请输入您的身份证号"
									placeholderClass="name_ph"
									v-model="forminfo.identity"
									border="none"
									@focus.stop="keyboard1"
							></u--input>
				</u-form-item>
				<u-form-item
					label="出生日期"
					prop="date"
					borderBottom
					ref="item1">
					<view class='date_text' @click="showdate" >
						<view class="date_time" :class="forminfo.date=='请选择您的出生日期'?'':'date_black'">{{forminfo.date}}</view>
						<view class="date_icon"><image src="http://cq.ymukj.cn/personal_data_im.png" alt=""></view>
					</view>
				</u-form-item>
				<u-form-item
					required='true'
					label="所在省"
					prop="province"
					borderBottom
					ref="item1">
					<view class='date_text' @click="changeaddress" >
						<view class="date_time" :class="forminfo.province=='请选择省份'?'':'date_black'">{{forminfo.province}}</view>
						<view class="date_icon"><image src="http://cq.ymukj.cn/register_select_icon.png" alt=""></view>
					</view>
				</u-form-item>
				<u-form-item
					required='true'
					label="所在经销单位"
					prop="province"
					borderBottom
					ref="item1">
					<view class='date_text' @click="changeunit" >
						<view class="date_time" :class="forminfo.unit=='请选择经销单位'?'':'date_black'">{{forminfo.unit}}</view>
						<view class="date_icon"><image src="http://cq.ymukj.cn/register_select_icon.png" alt=""></view>
					</view>
				</u-form-item>
				<u-form-item
					required='true'
					label="现任职务"
					prop="province"
					borderBottom
					ref="item1">
					<view class='date_text' @click="changeposition" >
						<view class="date_time" :class="forminfo.position=='请选择业务代表'?'':'date_black'">{{forminfo.position}}</view>
						<view class="date_icon"><image src="http://cq.ymukj.cn/register_select_icon.png" alt=""></view>
					</view>
				</u-form-item>
				<u-form-item
							required='true'
							label="所在销售据点"
							prop="name"
							borderBottom
							ref="item1"
				>
						<u--input
								placeholderStyle="color: #93969D"
								placeholder="请输入销售据点"
								v-model="forminfo.stronghold"
								border="none"
						></u--input>
				</u-form-item>
				<u-form-item
					required='true'
					label="从事汽车销售时间"
					prop="date"
					borderBottom
					ref="item1">
					<view class='date_text' @click="showtime1" >
						<view class="date_time" :class="forminfo.time1=='请选择时间'?'':'date_black'">{{forminfo.time1}}</view>
						<view class="date_icon"><image src="http://cq.ymukj.cn/register_select_icon.png" alt=""></view>
					</view>
				</u-form-item>
				<u-form-item
					required='true'
					label="从事福瑞卡销售时间"
					prop="date"
					borderBottom
					ref="item1">
					<view class='date_text' @click="showtime2" >
						<view class="date_time" :class="forminfo.time2=='请选择时间'?'':'date_black'">{{forminfo.time2}}</view>
						<view class="date_icon"><image src="http://cq.ymukj.cn/register_select_icon.png" alt=""></view>
					</view>
				</u-form-item>
			</u--form>
		</view>
		<view class="register_other">
			<view class="other_title">其他凭证</view>
			<u-upload
					:deletable="true"
					:fileList="fileList1"
					@afterRead="afterRead"
					@delete="deletePic"
					name="1"
					multiple
					:maxCount="10"
				>
				</u-upload>
		</view>
		<view  class="register_button">
			<button class='button_btn' @click="confirmper">提交审核</button>
		</view>
		<u-keyboard ref="uKeyboardidentity" mode="card" :show="identityshow" @change="valChange1" @backspace="backspace1" @confirm='keyboard1' @cancel='keyboard1'></u-keyboard>
		<u-datetime-picker ref="datetimePicker" :show="dateshow"  v-model="datavalue" mode="date" :minDate="Number(new Date())-365*100*24*3600*1000" :maxDate='Number(new Date())'
		@cancel="canceldata" @confirm="confirmdata" :formatter="formatter" ></u-datetime-picker>
		<u-picker :show="isaddress" ref="uPickeraddress" :columns="columns"  @confirm="confirmaddress" @cancel="canceladdress"></u-picker>
		<u-picker :show="isunit" ref="uPickerunit" :columns="columns2"  @confirm="confirmunit" @cancel="cancelunit"></u-picker>
		<u-picker :show="isposition" ref="uPickerposition" :columns="columns3"  @confirm="confirmposition" @cancel="cancelposition"></u-picker>
		<u-datetime-picker ref="datetimePicker2" :show="istimeshow1"  v-model="timevalue1" mode="year-month" :minDate="Number(new Date())-365*100*24*3600*1000" :maxDate='Number(new Date())'
		@cancel="canceltime1" @confirm="confirmtime1" :formatter="formatter" ></u-datetime-picker>
		<u-datetime-picker ref="datetimePicker3" :show="istimeshow2"  v-model="timevalue2" mode="year-month" :minDate="Number(new Date())-365*100*24*3600*1000" :maxDate='Number(new Date())'
		@cancel="canceltime2" @confirm="confirmtime2" :formatter="formatter" ></u-datetime-picker>
		<u-toast ref="uToast"></u-toast>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				forminfo:{
					name:'',
					sex:'男',
					identity:'',
					date:'请选择您的出生日期',
					province:'请选择省份',
					unit:'请选择经销单位',
					position:'请选择业务代表',
					stronghold:'',
					time1:'请选择时间',
					time2:'请选择时间',
					fileList1:[]
				},
				sex:['男','女'],
				identityshow:false,
				dateshow:false,
				datavalue:null,
				isaddress:false,
				isunit:false,
				isposition:false,
				istimeshow1:false,
				istimeshow2:false,
				timevalue1:null,
				timevalue2:null,
				columns:[
					['北京市','上海市','天津市','重庆市','河北省','山西省','内蒙古省','辽宁省','吉林省','黑龙江省','江苏省','浙江省','安徽省','福建省','江西省','山东省','河南省','湖北省','湖南省','广东省','广西省','海南省','四川省','贵州省','云南省','西藏省','陕西省','甘肃省','宁夏省','青海省','新疆省','香港','澳门','台湾'],
				],
				columns2:[
					['1','2','3','4','5','6','7','8','9','10','11','12']
				],
				columns3:[
					['总经理','品牌经理','二网经理','销售顾问','信息员']
				],
				fileList1: [
					{
						url:'http://cq.ymukj.cn/personal_data_im.png'
					}
					],
			}
		},
		methods:{
			getYMDHMS(timestamp) {
				let time = new Date(timestamp)
				let year = time.getFullYear()
				const month = (time.getMonth() + 1).toString().padStart(2, '0')
				const date = (time.getDate()).toString().padStart(2, '0')
				const hours = (time.getHours()).toString().padStart(2, '0')
				const minute = (time.getMinutes()).toString().padStart(2, '0')
				// const second = (time.getSeconds()).toString().padStart(2, '0')
			
				return year + '-' + month + '-' + date + ' ' + hours + ':' + minute
			},
			formatter(type, value){
				   if (type === 'year') {
				   	return `${value}年`
				   }
				   if (type === 'month') {
				   	return `${value}月`
				   }
				   if (type === 'day') {
				   	return `${value}日`
				   }
				   return value
			   },
			canceldata(){
				this.dateshow=false
			},
			confirmdata(e){
				this.datavalue=Number(new Date(this.getYMDHMS(e.value).slice(0,10)));
				this.forminfo.date=this.getYMDHMS(e.value).slice(0,10);
				this.dateshow=false;
			},
			showdate(){
				console.log(123)
				this.dateshow=true;
			},
			radioChange(n){
				console.log('性别', n);
			},
			keyboard1(){
				uni.hideKeyboard()
				this.identityshow=!this.identityshow;
			},
			valChange1(val){
				this.forminfo.identity += val;
			},
			backspace1(){
				if(this.forminfo.identity.length){
					this.forminfo.identity = this.forminfo.identity.substr(0, this.forminfo.identity.length - 1);
				}  
			},
			changeaddress(){
				this.isaddress=!this.isaddress
			},
			confirmaddress(value){
				this.isaddress=false
				this.forminfo.province=value.value[0]
				console.log(value.value[0])
			},
			canceladdress(){
				this.isaddress=false;
			},
			changeunit(){
				this.isunit=!this.isunit
			},
			confirmunit(value){
				this.isunit=false
				this.forminfo.unit=value.value[0]
				console.log(value.value[0])
			},
			cancelunit(){
				this.isposition=false
			},
			changeposition(){
				this.isposition=!this.isposition
			},
			confirmposition(value){
				this.isposition=false
				this.forminfo.position=value.value[0]
				console.log(value.value[0])
			},
			cancelposition(){
				this.isposition=false
			},
			showtime1(){
				this.istimeshow1=!this.istimeshow1
			},
			showtime2(){
				this.istimeshow2=!this.istimeshow2
			},
			canceltime1(){
				this.istimeshow1=false
			},
			canceltime2(){
				this.istimeshow2=false
			},
			confirmtime1(e){
				this.timevalue1=Number(new Date(this.getYMDHMS(e.value).slice(0,10)));
				this.forminfo.time1=this.getYMDHMS(e.value).slice(0,7);
				this.istimeshow1=false;
			},
			confirmtime2(e){
				this.timevalue2=Number(new Date(this.getYMDHMS(e.value).slice(0,10)));
				this.forminfo.time2=this.getYMDHMS(e.value).slice(0,7);
				this.istimeshow2=false;
			},
			// 删除图片
			deletePic(event) {
				this[`fileList${event.name}`].splice(event.index, 1)
			},	
			// 新增图片
			async afterRead(event) {
				// 当设置 mutiple 为 true 时, file 为数组格式，否则为对象格式
				let lists = [].concat(event.file)
				let fileListLen = this[`fileList${event.name}`].length
				lists.map((item) => {
					this[`fileList${event.name}`].push({
						...item,
						status: 'uploading',
						message: '上传中'
					})
				})
				for (let i = 0; i < lists.length; i++) {
					const result = await this.uploadFilePromise(lists[i].thumb)
					let item = this[`fileList${event.name}`][fileListLen]
					this[`fileList${event.name}`].splice(fileListLen, 1, Object.assign(item, {
						status: 'success',
						message: '',
						url: result
					}))
					fileListLen++
				}
			},	
			uploadFilePromise(url) {
				return new Promise((resolve, reject) => {
					let a = uni.uploadFile({
						url: 'http://192.168.2.21:7001/upload', // 仅为示例，非真实的接口地址
						filePath: url,
						name: 'file',
						formData: {
							user: 'test'
						},
						success: (res) => {
							setTimeout(() => {
								resolve(res.data.data)
							}, 1000)
						}
					});
				})
			},	
			showToast(e,type) {
				this.$refs.uToast.show({
						type:type,
						message:e
				})		
			},									
			validation(){
				this.isconfirm=false;
				if(!this.forminfo.name){
					this.showToast('姓名不能为空','error')
				}else if(!this.forminfo.identity){
					this.showToast('身份证号不能为空','error' )
				}else if(!this.forminfo.province=='请选择省份'){
					this.showToast('请选择省份','error')
				}else if(!this.forminfo.unit=='请选择经销单位'){
					this.showToast('请选择经销单位','error')
				}else if(!this.forminfo.position=='请选择业务代表'){
					this.showToast('请选择业务代表','error')
				}else if(!this.forminfo.stronghold){
					this.showToast('请填写销售据点','error')
				}else if(!this.forminfo.time1=='请选择时间'){
					this.showToast('请选择从事销售时间','error')
				}else if(!this.forminfo.time2=='请选择时间'){
					this.showToast('请选择从事福瑞卡销售时间','error')
				}else if(!/^[1-9]\d{5}(18|19|20)\d{2}((0[1-9])|(1[0-2]))(([0-2][1-9])|10|20|30|31)\d{3}[0-9Xx]$/.test(this.forminfo.identity)){
					this.showToast('身份证格式不正确','error')
				}else{
					this.showToast('提交成功','success')
					this.isconfirm=true;
				}
			},
			confirmper(){
				this.forminfo.fileList1=[];
				this.validation();
				for(let i=0;i<this.fileList1.length;i++){
						this.forminfo.fileList1.push(this.fileList1[i].url)
				}
				console.log(this.forminfo,this.isconfirm)
				if(this.isconfirm){
					console.log(123)
					uni.navigateTo({
						url: '/pages/dealers/dealers'
					});
				}
			},
		
		}
	}
</script>

<style lang="scss">

/deep/.register_form .u-form-item__body{
	flex-direction: row !important;
	justify-content: space-between !important;
	padding:30rpx 32rpx !important;
}
/deep/.register_form .u-form-item__body__left__content__label{
	font-size: 28rpx;
	font-family: PingFangSC-Regular, PingFang SC;
	font-weight: 400;
	color: #282D3B;
}
/deep/.register_form .u-input__content__field{
	font-size: 28rpx !important;
	font-family: PingFangSC-Regular, PingFang SC !important;
	font-weight: 400 !important;
	text-align: right !important;
}
/deep/.register_form .u-form-item__body__right{
	flex: none;
}
/deep/.register_form .u-form-item__body__left__content__required{
	color: #FF3B30;
}
/deep/.register_form .u-radio__icon-wrap{
	margin-right: 6rpx !important;
}
/deep/.register_form .u-radio{
	margin-left: 20rpx !important; 
}
/deep/.register_form .u-radio__text{
	font-size: 28rpx !important;
	font-family: PingFangSC-Regular, PingFang SC !important;
	font-weight: 400 !important;
	color: #525662 !important;
}
/deep/.register_form .u-form-item__body__left{
	width: auto !important; 
}
/deep/.register_other .u-upload__button{
	width: 92rpx;
	height: 120rpx;
	border-radius: 16rpx;
}
/deep/.register_other .u-upload__wrap__preview__image{
	width:156rpx !important;
	height: 120rpx !important;
}
/deep/.register_other .u-upload__wrap{
	flex-wrap: wrap;
	width: 600rpx !important;
}
/deep/.register_other .u-upload{
	flex-direction: row-reverse;
	justify-content: flex-end;
	width: 600rpx !important;
}
/deep/.register_other .u-upload__deletable{
	width: 32rpx;
	height: 32rpx;
	background: #D6D6D6;
	border-radius: 50%;
	transform: translate(30%,-30%);
}
/deep/.register_other .u-icon__icon{
	font-size: 26rpx !important;
	line-height: 32rpx !important;
	left: 50%;
	transform: translate(-60%);
}
/deep/.register_other .u-upload__wrap__preview{
	overflow: visible;
}
.register{
	.register_form{
		.date_text{
			display: flex;
			flex-direction: row;
			justify-content: space-between;
			align-items: center;
			.date_time{
				font-size: 28rpx;
				font-family: PingFangSC-Regular, PingFang SC;
				font-weight: 400;
				color: #93969D;
				margin-right: 20rpx;
			}
			.date_icon{
				width: 32rpx;
				height: 32rpx;
				image{
					width: 100%;
					height: 100%;
				}
			}
		}
		.date_black{
			color:#525662 !important;
		}
	}
	.register_other{
		padding: 0 30rpx;
		.other_title{
			padding:30rpx 0 ;
			font-size: 28rpx;
			font-family: PingFangSC-Regular, PingFang SC;
			font-weight: 400;
			color: #282D3B;
			line-height: 40rpx;
		}
	}
	.register_button{
		margin: 50rpx 0;
		width: 100%;
		height: 88rpx;
		button{
			width: 622rpx;
			height: 88rpx;
			background: linear-gradient(135deg, #FF541B 0%, #EC2113 100%);
			box-shadow: 0rpx 24rpx 24rpx -16rpx rgba(229, 2, 2, 0.5);
			border-radius: 53rpx;
			font-size: 28rpx;
			font-family: PingFangSC-Semibold, PingFang SC;
			font-weight: 600;
			color: #FFFFFF;
			line-height: 88rpx;
		}
	}
}
</style>
