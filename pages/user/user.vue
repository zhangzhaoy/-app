<template>
    <view class="content">
	<!-- 顶部自定义导航栏 -->	
<uni-nav-bar left-icon="back" status-bar="true" shadow="false" color="#008aff" title="个人中心" class="nav border-topBotton" @click-left="onClickLeft">
</uni-nav-bar>	
	
	<view class="user-index white border-topBotton">
		<navigator url=""  v-if="!hasLogin" @click="clickXiaoqu">
			<view class="user-botton1">
				<image src="/static/icon/logo.png" class="logo" mode="widthFix"></image>
				<view class="logo-ringht">
					<view class="user-view">未登录</view>
					<view class="bi"><image src="/static/icon/bi.png" mode="widthFix"></image>0<text>如何获取积分</text></view>
				</view>
				<text class="icon">></text>
			</view>			
		</navigator>
	</view>
	<!-- 管理我的小区 -->
	<view class="user-index white border-topBotton">
		<navigator url=""  v-if="!hasLogin" @click="clickXiaoqu">		
			<view class="user-botton1">
					<view class="user-view1">管理我的小区</view>
				<text class="icon">></text>
			</view>
		</navigator>
	</view>	
	<!-- 我的一呼百应 -->
	<view class="user-index white1 border-topBotton">
		<navigator url=""  v-if="!hasLogin" @click="clickXiaoqu">		
			<view class="user-botton1">
					<view class="user-view1">我的一呼百应</view>
				<text class="icon">></text>
			</view>
		</navigator>		
	</view>	
	<!-- 我的个人安保 -->
	<view class="user-index white1 border-topBotton">
		<navigator url=""  v-if="!hasLogin" @click="clickXiaoqu">		
			<view class="user-botton1">
					<view class="user-view1">我的个人安保</view>
				<text class="icon">></text>
			</view>
		</navigator>			
	</view>	
	<!-- 个人安全度 -->
	<view class="user-index white1 border-topBotton">
		<navigator url=""  v-if="!hasLogin" @click="clickXiaoqu">		
			<view class="user-botton1">
					<view class="user-view1">个人安全度</view>
				<text class="icon">></text>
			</view>
		</navigator>			
	</view>
	<!-- 设置 -->
	<view class="user-index white border-topBotton">
		<navigator url="./shezhi/shezhi">		
			<view class="user-botton1">
					<view class="user-view1">设置</view>
				<text class="icon">></text>
			</view>
		</navigator>
	</view>	
	
        <view class="btn-row">
            <button v-if="!hasLogin" type="primary" class="primary" @tap="bindLogin">登录</button>
            <button v-if="hasLogin" type="default" @tap="bindLogout">退出登录</button>
        </view>
    </view>
</template>

<script>
	import uniNavBar from "@/components/uni-nav-bar/uni-nav-bar.vue";	
    import {
        mapState,
        mapMutations
    } from 'vuex'

    export default {
        computed: {
            ...mapState(['hasLogin', 'forcedLogin'])
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
            ...mapMutations(['logout']),
            bindLogin() {
                uni.navigateTo({
                    url: '../login/login',
                });
            },
            bindLogout() {
                this.logout();
                /**
                 * 如果需要强制登录跳转回登录页面
                 */
                if (this.forcedLogin) {
                    uni.reLaunch({
                        url: '../login/login',
                    });
                }
            }
        },
		components: {uniNavBar}		
    }
</script>

<style>
@import url("user.css");
</style>
