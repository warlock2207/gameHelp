<template>
	<view class="box-bg">
		<uni-nav-bar>
			<view class="input-view">
				<uni-icons class="input-uni-icon" type="search" size="18" color="#999" />
				<input confirm-type="search" class="nav-bar-input" type="text" placeholder="搜索游戏" @click="search" />
			</view>
		</uni-nav-bar>
	
		<v-tabs v-model="current" :tabs="tabs" @change="changeTab" activeColor="#ffffff" pills=true pillsColor="#d81e06"
			pillsBorderRadius="50rpx"></v-tabs>
		
				<uni-waterfall>
					<!-- Swiper-mfw轮播图带视频 [仿马蜂窝APP首页轮播图] -->
					<FatFatMeng-Swiper-mfw
					:list="bannerList"
					:current="currentB"
					:autoplay="false"
					@change="change"
					></FatFatMeng-Swiper-mfw>
				</uni-waterfall>
			
		<sl-filter :themeColor="themeColor" :menuList="menuList" @result="result"></sl-filter>
		<view class="uni-list" style="margin-bottom: 32upx;">
					<block v-for="(item, index) in data" :key="index">
		                <list-good :data="item" :index="index" @click="to_detail" @change="_changeListGood">
		                   <!-- <view style="color: #007AFF;font-size: 20upx;">
		                    	其他内容({{data.size}})
		                    </view> -->
		                    <template slot="numbox">
		                    	{{data.size==-1?'到货提醒':data.size==-2?'抢购':data.size==-3?'停止销售':''}}
		                    </template>
		                </list-good>
		            </block>
				</view>
		</view>
	
</template>
<script>
	import slFilter from '@/components/songlazy-sl-filter/sl-filter/sl-filter.vue';
	import specialBanner from '@/components/EtherealWheat-banner/specialBanner.vue';
	import listGood from '@/components/wlp-list-good/wlp-list-good.vue';
	
	import {Swiper_mfw_index_data} from '@/uni_modules/FatFatMeng-Swiper-mfw/components/FatFatMeng-Swiper-mfw/index.js'
	export default {
		data() {
			return {
				current: 0,
				currentB: 0,
				tabs: ['热门游戏', '最新折扣', '即将过期', '折扣力度', '最佳口碑'],
				themeColor: '#000000',
				filterResult: '',
				menuList: [{
						'title': '任意折扣',
						'key': 'sort',
						'isSort': true,
						'detailList': [{
								'title': '任意折扣',
								'value': ''
							},
							{
								'title': '任意史低',
								'value': 'add_time'
							},
							{
								'title': '历史新低',
								'value': 'wages_up'
							}
						]
					}, {
						'title': '中文',
						'detailList': [{
							'title': '中文',
							'value': 'add_time'
						}]
					},
					{
						'title': '筛选',
						'detailTitle': '请选择职位类型（可多选）',
						'isMutiple': true,
						'key': 'jobType',
						'detailList': [{
								'title': '不限',
								'value': ''
							},
							{
								'title': '独占',
								'value': 'uni-app'
							},
							{
								'title': '港区',
								'value': 'java'
							},
							{
								'title': '日区',
								'value': 'web'
							},
							{
								'title': '角色扮演',
								'value': 'Android'
							}
						]
					}
				],
				bannerList: [/* {
					picture: 'http://mms0.baidu.com/it/u=2284267172,355355407&fm=253&app=138&f=PNG?w=616&h=384',
					title: '塞尔达传说',
					description: '塞尔达塞尔达塞尔达塞尔达',
					path: ''
				}, {
					picture: 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg1.gamersky.com%2Fupimg%2Fpic%2F2021%2F02%2F18%2Fsmall_202102180606184538.jpg&refer=http%3A%2F%2Fimg1.gamersky.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1662701915&t=dbdc33cd9ae11d5fe011b40bf68dfe0c',
					title: '异度之刃2',
					description: '花中樱，鱼乃鲷花中樱，鱼乃鲷',
					path: ''
				}, {
					picture: 'https://img0.baidu.com/it/u=4084545642,29127534&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500',
					title: '怪物猎人RISE',
					description: '一起狩猎吧',
					path: ''
				}, {
					picture: 'https://img1.baidu.com/it/u=4025108024,502327549&fm=253&fmt=auto&app=138&f=JPEG?w=825&h=500',
					title: '女神异闻录5',
					description: 'P5，天下第一',
					path: ''
				}, */ {
					Image:'https://img1.baidu.com/it/u=4025108024,502327549&fm=253&fmt=auto&app=138&f=JPEG?w=825&h=500',//轮播图(封面图)
					mp4:'',
					title:'女神异闻录5',//标题
					UserImage:'https://img1.baidu.com/it/u=4025108024,502327549&fm=253&fmt=auto&app=138&f=JPEG?w=825&h=500',// 用户头像
					UserName:'P5，天下第一',// 用户名
					UserGPS:'广州' // 当前所在的城市
				 },/* {
					Image:'https://n1-q.mafengwo.net/s16/M00/EB/2D/CoUBUmDlheiAdABtAAgo3xeAaaQ458.jpg?imageMogr2/thumbnail/!440x300r/strip/gravity/Center/crop/!440x300/quality/90',//轮播图(封面图)
					mp4:'',
					title:'一半风光一半人文，与你奔赴藏地找寻世界如初的模样',//标题
					UserImage:'https://p1-q.mafengwo.net/s10/M00/5C/55/wKgBZ1mRHV2APLX9AABt9unXidc25.jpeg?imageMogr2%2Fthumbnail%2F%21200x200r%2Fgravity%2FCenter%2Fcrop%2F%21200x200%2Fquality%2F90',// 用户头像
					UserName:'郭小yan',// 用户名
					UserGPS:'广州' // 当前所在的城市
				 } */
				 {
				 	Image: 'http://mms0.baidu.com/it/u=2284267172,355355407&fm=253&app=138&f=PNG?w=616&h=384',
				 	title: '塞尔达传说',
					UserImage:'https://img1.baidu.com/it/u=4025108024,502327549&fm=253&fmt=auto&app=138&f=JPEG?w=825&h=500',// 用户头像
				 	description: '塞尔达塞尔达塞尔达塞尔达',
				 	path: ''
				 }, {
				 	Image: 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg1.gamersky.com%2Fupimg%2Fpic%2F2021%2F02%2F18%2Fsmall_202102180606184538.jpg&refer=http%3A%2F%2Fimg1.gamersky.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1662701915&t=dbdc33cd9ae11d5fe011b40bf68dfe0c',
				 	title: '异度之刃2',
				 	description: '花中樱，鱼乃鲷花中樱，鱼乃鲷',
				 	path: ''
				 }, {
				 	Image: 'https://img0.baidu.com/it/u=4084545642,29127534&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500',
				 	title: '怪物猎人RISE',
				 	description: '一起狩猎吧',
				 	path: ''
				 }, {
				 	Image: 'https://img0.baidu.com/it/u=4084545642,29127534&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500',
				 	title: '怪物猎人RISE',
				 	description: '一起狩猎吧',
				 	path: ''
				 }
				 ],
				swiperConfig: {
					indicatorDots: true,
					indicatorColor: 'rgba(255, 255, 255, .4)',
					indicatorActiveColor: 'rgba(255, 255, 255, 1)',
					autoplay: false,
					interval: 3000,
					duration: 300,
					circular: true,
					previousMargin: '58rpx',
					nextMargin: '58rpx'
				},
				data: [
				                    {
				                        title: '三位一体1',
				                        titleSub: '冒险/动作/益智',
				                        imgUrl: '/static/temp/1.png',
				                        sku: [{name:'史低'},{name:'中文'}],
				                        label: '折扣',
				                        price: '9.9',
				                        originalPrice: '45',
				                        size: 3
				                    },
				                    {
				                        title: '三位一体2',
				                        titleSub: '冒险/动作/益智',
				                        imgUrl: '/static/temp/1.png',
				                        sku: [{name:'史低'},{name:'中文'}],
				                        label: '折扣',
				                        price: '9.9',
				                        originalPrice: '45',
				                        size: 1
				                    },
				                    {
				                        title: '三位一体3',
				                        titleSub: '冒险/动作/益智',
				                        imgUrl: '/static/temp/1.png',
				                        price: '9.9'
				                    }, {
				                        title: '三位一体2',
				                        titleSub: '冒险/动作/益智',
				                        imgUrl: '/static/temp/1.png',
				                        sku: [{name:'史低'},{name:'中文'}],
				                        label: '折扣',
				                        price: '9.9',
				                        originalPrice: '45',
				                        size: 1
				                    },
									{
									    title: '三位一体2',
									    titleSub: '冒险/动作/益智',
									    imgUrl: '/static/temp/1.png',
									    sku: [{name:'史低'},{name:'中文'}],
									    label: '折扣',
									    price: '9.9',
									    originalPrice: '45',
									    size: 1
									}
				                ]
			}
		},
		components: {
			slFilter,
			specialBanner,
			listGood
		},
		methods: {
			search() {
				uni.redirectTo({
					url: "/pages/tarbar/search/search"
				})
			},
			change(e){
				this.currentB = e.current
			},
			to_detail() {
				/* uni.redirectTo({
					url: "/pages/tarbar/detail/detail"
				}) */
				console.info(1111);
			},
			
		}
	}
</script>

<style lang="scss">
	$nav-height: 30px;

	.box-bg {
		background-color: #F5F5F5;
		padding: 5px 0;
	}

	.input-view {
		/* #ifndef APP-PLUS-NVUE */
		display: flex;
		/* #endif */
		flex-direction: row;
		width: 600rpx;
		flex: 1;
		background-color: #f8f8f8;
		height: $nav-height;
		border-radius: 15px;
		padding: 0 15px;
		flex-wrap: nowrap;
		margin: 7px 0;
		line-height: $nav-height;
	}

	.input-uni-icon {
		line-height: $nav-height;
	}

	.nav-bar-input {
		height: $nav-height;
		line-height: $nav-height;
		/* #ifdef APP-PLUS-NVUE */
		width: 370rpx;
		/* #endif */
		padding: 0 5px;
		font-size: 12px;
		background-color: #f8f8f8;
	}
	  .pageList__row--wrap{
	        display: flex;
	        flex-wrap: wrap;
	        padding: 8upx;
	    }
	    
	    .uni-form-item .title {
	    	padding: 20upx 0;
	    }
</style>
