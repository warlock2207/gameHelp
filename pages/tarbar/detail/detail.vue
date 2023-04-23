<template>
	<view>
	<v-tabs v-model="current" :tabs="tabs"  activeColor="#000000" pills:true pillsColor="#d81e06"
		pillsBorderRadius="50rpx">
	</v-tabs>
		<view><carousel :img-list="imgList" url-key="url" @selected="selectedBanner"/></view>
				<view class="example-body">
							   <view>
									<text> <font style="font-size:45rpx;font-family:'黑体';font-weight: bold;">泰拉瑞亚</font> </text>
									<view>
										trrair
									</view>
									
								</view>
								<view class="box_right">
									 <image class="grade" src="/static/icon/hexagon.png"></image>
									 <text class = "number">2.0</text>
								</view>
							</view>
							<view class="example-body2">
								<view class="ktetx">
								<font class="titletx">游戏</font>
								</view>
								<view class="otherInfo">
									<font style="color: #797979;font-size:22rpx">2018-11-06/多人游玩/325M</font>
								</view>
							</view>
							<view class="example-body2">
									 <image class="lable-grade" src="/static/icon/label_image.png"></image>
									 <view class="label-info">
										 竞速
									 </view>
									 <view class="label-info">
									 	多人
									 </view>
									 <view class="label-info">
									 	其他
									 </view>
							</view>
							<view class="info-all">
								
							</view>
		  
			<!-- <view>
				<text class="uni-text">uni-app是一个使用Vue.js开发所有前端应用的框架，开发者编写一套代码，可发布到iOS、Android、H5、以及各种小程序（微信/支付宝/百度/头条/QQ/钉钉）等多个平台。即使不跨端，uni-app同时也是更好的小程序开发框架。DCloud公司拥有370万开发者用户，旗下uni-app有5万+案例、900款插件、50+微信/qq群，并且被阿里小程序工具内置，开发者可以放心选择。</text>
			</view>	  -->
	</view>
</template>

<script>
	import carousel from '@/components/vear-carousel/vear-carousel'
	import uniTitle from '@/uni_modules/uni-title/components/uni-title/uni-title.vue'
	export default {
		data() {
			return {
				tabs: ['游戏', '评价'],
				current: 0,
				imgList: [{
				                    url: 'https://img1.baidu.com/it/u=4025108024,502327549&fm=253&fmt=auto&app=138&f=JPEG?w=825&h=500',
				                    id: 1
				                },{
				                    url: 'https://img0.baidu.com/it/u=4084545642,29127534&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500',
				                    id: 2
				                },{
				                    url: 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg1.gamersky.com%2Fupimg%2Fpic%2F2021%2F02%2F18%2Fsmall_202102180606184538.jpg&refer=http%3A%2F%2Fimg1.gamersky.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1662701915&t=dbdc33cd9ae11d5fe011b40bf68dfe0c',
				                    id: 3
				                },{
				                    url: 'http://mms0.baidu.com/it/u=2284267172,355355407&fm=253&app=138&f=PNG?w=616&h=384',
				                    id: 4
				                },]
				}
			},
		methods: {
			 selectedBanner(item, index) {
			                console.log('🥒', item, index)
			            }
		},
		components: {
			carousel,uniTitle
		},
	}
</script>

<style lang="scss">
	.example-body {
		padding: 5px;
		left: 16upx;
		display: inline; 
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding-right: 12px;
	}
	.example-body2 {
		padding: 5px;
		left: 16upx;
		display: flex;
		flex-direction: row;
		align-items: center;
		padding-right: 12px;
	}
	.box {
		/* #ifndef APP-NVUE */
		display:flex;
		/* #endif */
	}
	.box_right {
		/* #ifndef APP-NVUE */
		left: 85%;
		display:flex;
		/* #endif */
	}
	.box_right .number {
	            position: absolute;
	            left: 89.3%;
	            //top: -12px;
	            //background-color: red;
	            color: #fff;
	            line-height: 32px;
	            width: 23px;
	            border-radius: 12px;
	            text-align: center;
	            font-size: 17px;
	        }
	.uni-text {
		font-size: 14px;
		line-height: 12px;
		color: #333;
	}
	.grade{
		width: 35px;
		height: 35px;
		text-align: center;
	}
	.lable-grade{
		width: 30px;
		height: 22px;
		text-align: center;
	}
	
	
	 .ktetx {
	    border: 1.2px solid red;
	     height: 18px;
	     width: 34px;
	    border-radius: 10px;
		align-items:center;
		justify-content: center;
	 }
	 .label-info {
		border: 1.1px;
	    background-color: #EEEEEE;
	    height: 18px;
	    width: 34px;
	    border-radius: 5px;
		font-size: 18rpx;
		align-items:center;
		display: flex;
		align-items: center;
		vertical-align: center;
		justify-content: center;
		flex-direction: row;
		margin-left: 4px;
	 }
	 .titletx{
		 color: #ff0000;
		 font-size:18rpx;
		 align-items:center;
		 display: flex;
		 align-items: center;
		 vertical-align: center;
		 justify-content: center;
		 flex-direction: row;
	 }
	 .otherInfo{
	 	margin-left: 10rpx;
		align-items: center;
		display:block;
	 }
	.info-all{
		background-color: #EEEEEE;
		height: 50px;
		width: 350px;
		border-radius: 5px;
		left: 16upx;
	}
	.info-all{
		background-color: #EEEEEE;
		padding-left: 5px;
		padding-right: 5px;
	}
</style>