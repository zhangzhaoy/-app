<template>
	<view>
	<!-- 顶部自定义导航栏 -->	
<uni-nav-bar left-icon="back" status-bar="true" shadow="false" color="#008aff" title="设置" class="nav border-topBotton" @click-left="onClickLeft">
</uni-nav-bar>

	<!-- 意见反馈 -->
	<view class="user-index white border-topBotton">
		<navigator url=""  v-if="!hasLogin" @click="clickXiaoqu">		
			<view class="user-botton1">
					<view class="user-view1">意见反馈</view>
				<text class="icon">></text>
			</view>
		</navigator>
	</view>		
	<!-- 检查新版本 -->
	<view class="user-index white1 border-topBotton">
		<navigator url=""  v-if="!hasLogin" @click="clickXiaoqu">		
			<view class="user-botton1">
					<view class="user-view1">检查新版本</view>
				<view class="banben"><text class="text-i">1.02</text>  <text class="icon1">></text></view>
			</view>
		</navigator>
	</view>	
	<!-- 分享安居APP -->
	<view class="user-index white border-topBotton">
		<navigator url=""  v-if="!hasLogin" @click="clickXiaoqu">		
			<view class="user-botton1">
					<view class="user-view1">分享安居APP</view>
				<text class="icon">></text>
			</view>
		</navigator>
	</view>
	<!-- 关于安居APP -->
	<view class="user-index white border-topBotton">
		<navigator url=""  v-if="!hasLogin" @click="clickXiaoqu">		
			<view class="user-botton1">
					<view class="user-view1">关于安居APP</view>
				<text class="icon">></text>
			</view>
		</navigator>
	</view>

	<view class="btn-row">
		<button v-if="hasLogin" type="primary" class="primary" @tap="bindLogin">登录</button>
		<button v-if="!hasLogin" type="default" class="primary" @tap="bindLogout">退出登录</button>
	</view>				
			
	</view>
</template>

<script>
	import uniNavBar from "@/components/uni-nav-bar/uni-nav-bar.vue";	
	export default {
		
		data() {
			return {
				
			}
		},
		methods: {
			onClickLeft(){
				uni.navigateBack({
					delta: 1,
					animationType: 'pop-out',
					animationDuration: 200
				});				
				//console.log(555)
			}			
		},
		components: {uniNavBar}			
	}
</script>

<style>
@import url("../user.css");
</style>
