<template>
    <view>

        <view class="free_card_box" v-for="(item, index) in teaList" :key="index">
            <view class="free_card_img">
                <image :src="item.teacher_logo" mode="" />
            </view>

            <view class="free_card_text">
                <view class="free_card_T">{{ item.limitName }}</view>
                <view class="free_card_info">
                    <view class="free_card_info_text">
                        <view class="info_text1">{{ item.teacher_name }}{{ item.teacher_job }}</view>
                        <view>{{ item.limitNum }}人学过</view>
                    </view>
                    <view class="free_card_info_btn" v-if="item.baoming == '立即学习'">{{ item.baoming }}</view>
                    <view class="free_card_info_btn free_card_info_btn1" v-else>{{ item.baoming }}</view>
                </view>
            </view>
        </view>

    </view>
</template>

<script>
export default {
    data() {
        return {
            teaList: []
        }
    },
    mounted() {
        uni.request({
            url: 'https://yapi.pro/mock/120455/free',
            success: (res) => {
                this.teaList = res.data.data
            },
        })
    },
}
</script>

<style lang="scss">
.free_card_box {
    display: flex;
    padding: 20rpx 0;
    margin: 20rpx;
    margin-bottom: 30rpx;
    border-radius: 10px;
    box-shadow: 0 0 5px 1px rgba($color: #000000, $alpha: 0.1);
    box-sizing: border-box;
    justify-self: center;
    align-items: center;

    .free_card_img {
        flex-shrink: 0;
        width: 91rpx;
        height: 91rpx;
        border-radius: 100%;
        margin: 0 30rpx;

        image {
            width: 100%;
            height: 100%;
            border-radius: 100%;
        }
    }

    .free_card_text {
        width: 100%;
        display: flex;
        box-sizing: border-box;
        flex-direction: column;
        padding: 0 30rpx 0 0;

        .free_card_T {
            font-size: 30rpx;
            text-overflow: ellipsis;
            overflow: hidden;
            margin: 20r px 0;
        }
    }

    .free_card_info {
        width: 100%;
        display: flex;
        box-sizing: border-box;
        flex-direction: row;
        font-weight: nowrap;
        justify-content: space-between;

        .free_card_info_text {
            width: 60%;
            overflow: hidden;
            font-size: 30rpx;
            color: #666;

            .info_text1 {
                height: 40rpx;
                font-size: 28rpx;
                overflow: hidden;
            }
        }

        .free_card_info_btn {
            width: 200rpx;
            height: 65rpx;
            text-align: center;
            line-height: 65rpx;
            border-radius: 34px;
            background-color: pink;
            color: white;
            font-size: 32rpx;
            margin-top: 20rpx;
        }

        .free_card_info_btn1 {
            background-color: #ddd;
        }
    }
}
</style>   