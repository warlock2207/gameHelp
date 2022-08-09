### 使用方法

```vue
<template>
	<view>
		<searchPanel :placeholder="placeholder" :hotKeywords="hotKeywords" @search="search"
			@clearKeyword="clearKeyword" @clearHistory="clearHistory" @fillKeyword="fillKeyword" />
	</view>
</template>

<script>
	import searchPanel from '@/uni_modules/cshaptx4869/searchPanel/searchPanel'

	export default {
		data() {
			return {
				placeholder: '三鲜汤',
				hotKeywords: ['酸菜鱼', '糖醋排骨']
			}
		},
		methods: {
			search(keyword) {
				console.log('点击了搜索按钮:', keyword)
			},
			clearKeyword() {
				console.log('点击了清除关键字按钮')
			},
			clearHistory() {
				console.log('点击了清空历史记录按钮')
			},
			fillKeyword(keyword) {
				console.log('点击了关键字:', keyword)
			}
		},
		components: {
			searchPanel
		},
	}
</script>

<style>

</style>
```

**参数说明：**

- borderColor：搜索按钮边框颜色
- textColor： 搜索按钮文本颜色
- searchName：搜索按钮内容
- showMore：是否显示历史记录和热门搜索
- placeholder：输入框placeholder
- hotKeywords：热门搜索关键字
- historyStoreKey：搜索历史本地存储key
- maxHistoryKeywordNumber：最大存储历史搜索关键字个数
- @search：点击搜索回调，会传递当前检索关键字
- @clearKeyword：点击清除检索关键字回调
- @clearHistory：点击清除搜索历史回调
- @fillKeyword：点击关键字回调