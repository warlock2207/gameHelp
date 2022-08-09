<template>
    <view>
        <searchPanel :placeholder="placeholder" :hotKeywords="hotKeywords" @search="search"
            @clearKeyword="clearKeyword" @clearHistory="clearHistory" @fillKeyword="fillKeyword" @textColor="textColor"/>
    </view>
</template>

<script>
    import searchPanel from '@/uni_modules/cshaptx4869-search/components/cshaptx4869-search/cshaptx4869-search'

    export default {
        data() {
            return {
                placeholder: '请输入游戏名',
                hotKeywords: ['塞尔达', '上古卷轴'],
				textColor:'#f8f8f8'
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