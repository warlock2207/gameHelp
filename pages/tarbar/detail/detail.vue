<template>
	<view>
	<v-tabs v-model="current" :tabs="tabs" @change="changeTab" activeColor="#ffffff" pills=true pillsColor="#d81e06"
		pillsBorderRadius="50rpx"></v-tabs>
		  <carousel :img-list="imgList" url-key="url" @selected="selectedBanner"/>
		  </view>
</template>

<script>
	import carousel from '@/components/vear-carousel/vear-carousel'
	export default {
		data() {
			return {
				tabs: ['游戏', '评价'],
				current: 0,
				imgList: [{
				                    url: 'https://img1.baidu.com/it/u=4025108024,502327549&fm=253&fmt=auto&app=138&f=JPEG?w=825&h=500',
				                    id: 1
				                },{
				                    url: 'https://img1.baidu.com/it/u=4025108024,502327549&fm=253&fmt=auto&app=138&f=JPEG?w=825&h=500',
				                    id: 2
				                },{
				                    url: 'https://img1.baidu.com/it/u=4025108024,502327549&fm=253&fmt=auto&app=138&f=JPEG?w=825&h=500',
				                    id: 3
				                },{
				                    url: 'https://img1.baidu.com/it/u=4025108024,502327549&fm=253&fmt=auto&app=138&f=JPEG?w=825&h=500',
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
			carousel
		},
	}
</script>

<style>
</style>