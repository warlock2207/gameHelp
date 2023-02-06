<template>
	<view>
	<v-tabs v-model="current" :tabs="tabs"  activeColor="#000000" pills:true pillsColor="#d81e06"
		pillsBorderRadius="50rpx">
	</v-tabs>
		<view><carousel :img-list="imgList" url-key="url" @selected="selectedBanner"/></view>
		  <view class="example-body">
				<view class="box" style="left: 16upx;">
					<text>泰拉瑞亚</text>
					<view class="box" >
						<text >trrair</text>
					</view>
					<view class="box" >
						<text >2018-11-06/325M</text>
					</view>
				</view>
				<view class="box_right">
					 <image class="grade" src="/static/icon/hexagon.png"></image>
					 <text class = "number">2.0</text>
				</view>
			</view>
			<view>
				<text class="uni-text">uni-app是一个使用Vue.js开发所有前端应用的框架，开发者编写一套代码，可发布到iOS、Android、H5、以及各种小程序（微信/支付宝/百度/头条/QQ/钉钉）等多个平台。即使不跨端，uni-app同时也是更好的小程序开发框架。DCloud公司拥有370万开发者用户，旗下uni-app有5万+案例、900款插件、50+微信/qq群，并且被阿里小程序工具内置，开发者可以放心选择。</text>
			</view>	  
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
		/* #ifndef APP-NVUE */
		/* #endif */
		padding: 2px;
		left: 16upx;
		display: inline; 
		display: flex;
	}
	.box {
		/* #ifndef APP-NVUE */
		display: block;
		/* #endif */
	}
	.box_right {
		/* #ifndef APP-NVUE */
		display: block;
		margin-left: 220px;	
		/* #endif */
	}
	.box_right .number {
	            position: absolute;
	            left: 75%;
	            //top: -12px;
	            //background-color: red;
	            color: #fff;
	            line-height: 28px;
	            width: 23px;
	            border-radius: 12px;
	            text-align: center;
	            font-size: 16px;
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
</style>