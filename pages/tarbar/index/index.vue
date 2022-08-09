<template>
		<view class="box-bg" >
			<uni-nav-bar>
				<view class="input-view">
					<uni-icons class="input-uni-icon" type="search" size="18" color="#999" />
					<input confirm-type="search" class="nav-bar-input" type="text" placeholder="搜索游戏"
						@click="search" />
				</view>
			</uni-nav-bar>
			<v-tabs v-model="current" :tabs="tabs" @change="changeTab" activeColor="#ffffff" pills=true pillsColor="#d81e06"
			 pillsBorderRadius="50rpx"></v-tabs>
			<sl-filter :themeColor="themeColor" :menuList="menuList" @result="result"></sl-filter>
		</view>
</template>
<script >
	import slFilter from '@/components/songlazy-sl-filter/sl-filter/sl-filter.vue';
	export default {
		data() {
			return {
				 current: 0,
				 tabs: ['热门游戏', '最新折扣', '即将过期', '折扣力度', '最佳口碑'],
				 themeColor: '#000000',
				 filterResult: '',
				 menuList: [
					 {
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
					 },{
						 'title': '中文',
						 'detailList': [{'title': '中文',
					 			'value': 'add_time'}]
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
				 				]
				 			  	
								
				}
		},
		components: {
		   slFilter
		},
		methods: {
			search(){
				uni.redirectTo({
                    url:"/pages/tarbar/search/search"
                })
			}
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
</style>
