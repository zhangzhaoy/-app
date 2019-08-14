<template>
	<view>
	<!-- 顶部自定义导航栏 -->	
<uni-nav-bar left-icon="back" status-bar="true" shadow="false" color="#008aff" title="安居门卫介绍" class="nav border-topBotton" @click-left="onClickLeft">
</uni-nav-bar>
<!-- 内容页面 -->
	<view class="jieshao">
		<view class="center">
			<video src="https://img-cdn-qiniu.dcloud.net.cn/uniapp/doc/uni-app20190127.mp4" controls></video>
			<view class="neirong">
				<view class="menwei-p">安居门卫是一项来访视频确认服务,访客到来
	时,将视频通知到您的手机,您可确认是否允
	许进入。</view>
				<view class="menwei-p">我们小区已经启用“安居门卫”来访视频确认
	服务,本功能需要向我物业管理处申请并确
	认,方可开通使用</view>				
			</view>
			<!-- 你尚未登录-->
			<view class="denlu">
				你尚未登录，请先登录安居宝。
			</view>
			<view class="botton">
					<navigator url="/pages/login/login">
						<button type="primary">登录</button>
					</navigator>

					<button type="primary" @tap="Reg">我要注册</button>	
			</view>
			<!-- 底部介绍 -->
			<view class="botton-jieshao">
				<navigator url="" v-if="!hasLogin" @click="clickXiaoqu">
					<text>个人保镖介绍</text>
				</navigator>
				<navigator url="" v-if="!hasLogin" @click="clickXiaoqu">
					<text>一呼百应介绍</text>
				</navigator>
			</view>
		</view>
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
			clickXiaoqu(){
            if (!this.hasLogin) {
                uni.showModal({
                    title: '温馨提示',
                    content: '您未登录，需要登录后才能继续',
                    /**
                     * 如果需要强制登录，不显示取消按钮
                     */
                    showCancel: !this.forcedLogin,
                    success: (res) => {
                        if (res.confirm) {
							/**
							 * 如果需要强制登录，使用reLaunch方式
							 */
                            if (this.forcedLogin) {
                                uni.reLaunch({
                                    url: '../login/login'
                                });
                            } else {
                                uni.navigateTo({
                                    url: '../login/login'
                                });
                            }
                        }
                    }
                });
            }				
				console.log("小区信息-请登录注册！")
			} ,			
			onClickLeft(){
				uni.navigateBack({
					delta: 1,
					animationType: 'pop-out',
					animationDuration: 200
				});				
				//console.log(555)
			},
			ClickBotton(){
				uni.navigateTo({
					url: '../login/login'
				});
			},
			Reg(){
				uni.navigateTo({
					url: '../reg/reg'
				});				
			}
		},
		components: {uniNavBar}
	}
</script>
<style>
@import url("./index-menwei.css");
.center {margin-bottom: 0;}
/* #ifdef APP-PLUS */
.center video {margin-top: 100upx;}
/* #endif */
</style>
