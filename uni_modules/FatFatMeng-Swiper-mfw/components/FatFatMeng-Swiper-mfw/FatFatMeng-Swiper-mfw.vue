<template>
	<!-- 轮播图 -->
	<view class="Swiper-mfw-index-box">
		<view class="Swiper-mfw-index Swiper-box">
			<swiper class="Swiper-mfw"
			:circular="true"
			:indicator-dots="false" 
			:autoplay="autoplay" 
			:interval="3000" 
			:duration="1000"
			:current="current"
			:disable-touch="disable_touch"
			@change="change"
			>	
				<!-- 只需要前5条数据 -->
				<swiper-item class="swiper-mfw-item"
				v-if="index <= 4"
				v-for="(item,index) in list"
				:key="index"
				>	
					<!-- /*
					 1. 这里不需要用api控制暂停视频
					 2. 因为video标签上加了v-if="current==index"
					 3. 当current == index时才会创建视频组件
					 4. 否current != index则就销毁视频
					 */ -->
					<!-- 如果有视频，则显示视频-->
					<template v-if="item.mp4 && current==index">
						<video class="ImageVideo"
						:id="'ImageVideo'+index"
						:ref="'ImageVideo'+index"
						:src="item.mp4"
						:loop="true"
						:muted="false"
						:autoplay="current==index ? true : false"
						:controls="false"
						:show-fullscreen-btn="false"
						:show-play-btn="false"
						:enable-progress-gesture="false"
						:play-strategy="0"
						:poster="item.Image"
						></video>
					</template>
					<!-- 否则显示图片 -->
					<image v-else :src="item.Image" class="Image" mode="aspectFill"></image>
					
				</swiper-item>
			</swiper>
			<!-- 指示器 [Top] -->
			<view v-if="true" class="Swiper-indicator-box indicator-Top-box">
				<!-- Top顶部 [今日首推-盒子] -->
				<view class="Top-date-hot">
					<!-- 左边盒子 - 日 -->
					<view class="left-date-ri">
						<text class="date-ri-text text app-ttf">07</text>
					</view>
					<!-- 中间盒子 - 年，月 -->
					<view class="conter-date-nianyue">
						<!-- 左边 黄色占位宽度盒子 -->
						<view class="left-width-bgcolor"></view>
						<!-- 右边 年月盒子 -->
						<view class="right-date-nianyue">
							<!-- 顶部 月份 [英文显示] -->
							<text class="Top-yue-usa text">AUG</text>
							<text class="Bottom-nian text">2023</text>
						</view>
					</view>
					<!-- 右边盒子 - 今日首推 -->
					<view class="right-hot-ttf">
						<text class="text hot-text app-ttf">热门游戏</text>
					</view>
				</view>
			</view>
			<!-- 指示器 [Bottom] -->
			<view v-if="true" class="Swiper-indicator-box indicator-Btoom-box">
				<!-- bottom底部 [详情-盒子] -->
				<view class="Bottom-datall">
					<!-- 指示器 [轮播信息 -> 标题,用户,头像,所在地] -->
					
					<!-- 指示器 [左边图片列表+右边按钮] -->
					<view class="Swiper-indicator-Bottom">
						<!-- 左边 -->
						<view class="Bottom-left-Imagelist">
							<!-- 只需要前5条数据 -->
							<!-- 指示图(小图模式) -->
							<view class="Bottom-item"
							v-if="Number(index) <= 4"
							:class="current==index ? 'current':'no'"
							v-for="(item,index) in list"
							:key="index"
							
							@click="SwiperIndTap(index)"
							>
								<image :src="item.Image" class="Image" mode="aspectFill"></image>
							</view>
						</view>
						<!-- 右边 -->
					
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"FatFatMeng-Swiper-mfw",
		props:{
			// 轮播图 数据列表
			list:{
				type:Array,
				default:[]
			},
			// 当前选中的项(指示器坐标位置)
			current:{
				type:Number,
				default:0
			},
			// 是否自动轮播
			autoplay:{
				type:Boolean,
				default:false
			}
		},
		data() {
			return {				
				// 是否禁止用户 touch 操作
				disable_touch: false,//touch 用户划动引起swiper变化。
			};
		},
		watch:{
			
		},
		methods:{
			// current 改变时会触发 change 事件，event.detail = {current: current, source: source}
			change(e) {
				let index = e.detail.current
				let event = {
					current: index
				}
				this.$emit('change',event)
			},
			// 手动点击了指示器[小图模式]
			SwiperIndTap(e){
				let index = e
				let event = {
					current: index
				}
				this.$emit('change',event)
			},
		},
		beforeCreate(){
			// #ifdef APP-PLUS
			const domModule = weex.requireModule('dom');
			// APP NVUE下 加载字体图标
			domModule.addRule('fontFace', {
				fontFamily: 'appiconfont',
				src: "url('http://at.alicdn.com/t/font_2582495_l8bsl3n1qme.ttf')"
			});
			// 自定义字体,不是icons字体图标
			domModule.addRule('fontFace', {
				fontFamily: 'appttf',
				src: "url('https://vkceyugu.cdn.bspapp.com/VKCEYUGU-6f9528be-c345-44ba-b6fd-591d2d036aec/9768b86a-b79c-41bc-9305-c42785200f0d.ttf')"
			});
			// #endif
		}
	}
</script>

<style lang="scss" scoped>
	@import "./Swiper-mfw-index.scss";
</style>
<style lang="scss">
	@import '@/uni_modules/FatFatMeng-Swiper-mfw/static/css/iconfont.css';
	.app-iconfont,.nvueiconfont {
		/* #ifdef APP-PLUS  */
	    font-family: appiconfont;
		/* #endif */
		font-size: 16px;
		color: #333;
		
	}
	.app-ttf{
		/* #ifdef APP-PLUS  */
		font-family: appttf;
		/* #endif */
		font-size: 16px;
	}
</style>