<template>
    <view class="content">

        <view v-if="!hasLogin" class="hello">
            <view class="index-botton">
				<view class="botton-1">
					<view class="index-h3">
					<navigator class="" url="/">开通安居门卫<text>∨</text></navigator>		
					</view>
					<navigator url="/">
						<image src="/static/icon/zhong.png" mode="widthFix"></image>
					</navigator>
					<navigator url="/">
						<image src="/static/icon/mao9.png" mode="widthFix"></image>		
					</navigator>
				</view>
				<view class="botton-2 white">
有时候你会发现,自己的内心是需要得到安慰的。只身一人在陌生的城市里,给人温暖的小熊成为我内心的倾听者,陪伴着我一起走过无数的圣诞节。
				</view>
				<view class="botton-3 white">
					<navigator url="../index-menwei/index-menwei">
						<image src="/static/icon/wo.png" mode="widthFix"></image>
						<view class="">安居宝</view>
					</navigator>
					<navigator url="/" v-if="!hasLogin" @click="clickXiaoqu">
						<image src="/static/icon/news.png" mode="widthFix"></image>
						<view class="">小区信息</view>								
					</navigator>
					<navigator url="/pages/user/user">
						<image src="/static/icon/geren.png" mode="widthFix"></image>
						<view class="">个人中心</view>
					</navigator>										
				</view>
            </view>
        </view>
    </view>
</template>

<script>
    import {
        mapState
    } from 'vuex'

    export default {
        computed: mapState(['forcedLogin', 'hasLogin', 'userName']),
        onLoad() {
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
			} 
		}
    }
</script>

<style>
@import url("./index.css");	
    .hello {
        display: flex;
        flex: 1;
        flex-direction: column;
    }

    .title {
        color: #8f8f94;
        margin-top: 50upx;
    }

    .ul {
        font-size: 30upx;
        color: #8f8f94;
        margin-top: 50upx;
    }

    .ul>view {
        line-height: 50upx;
    }
</style>
