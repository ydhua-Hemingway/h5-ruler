<template>
	<view class="content">
		<view v-for='item,index in new Array(windowWidthMm)' class="sub" :key="index">
			<img class="image" src="../../static/1mm.png" alt="">
			<view  :class='[!(index%10)?"long":"sort","line"]'></view>
			<view v-if="!(index%10)" class="sign">{{Math.round(index/10)}}</view>
		</view>
		<view>{{windowWidthMm}}</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				windowWidthMm: 0
			}
		},
		onLoad() {
			//获取手机屏幕宽度
			let windowWidth = 0;
			//只支持app h5 微信
			// #ifdef APP||MP-WEIXIN||H5
			windowWidth = uni.getWindowInfo().windowWidth;
			// #endif
			
			//根据单位换算
			this.windowWidthMm = Math.round(windowWidth/37.8*10);
			console.log(this.windowWidthMm,'windowWidthMm')
			//添加dom
			
		},
		methods: {

		}
	}
</script>

<style>
	*{
		margin:0;
		padding:0;
	}
	.content{
		height:100px;
		width:100%;
		float:left;
		overflow: hidden;
	}
	.line{
		display:inline-block;
		width:1px;
		/* margin-right:calc( 1mm - 1px ); */
		background:#000;
		position:absolute;
		top:0;
		left:0;
	}
	.sub{
		position:relative;
		display:inline-block;
		height:100px;
		vertical-align: top; 
	}
	.image{
		display:inline-block;
	}
	.long{
		height:100px;
		/* position:relative; */
	}
	.sort{
		height:50px;
	}
	.sign{
		position:absolute;
		left:0;
		bottom:0;
	}
</style>
