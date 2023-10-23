<template>
    <view class="course_jieshao_box">
        <!-- <image src="" mode="widthFix" /> -->
        <video src="/static/video.mp4" autoplay loop></video>
    </view>
</template>

<script>
export default {
    data() {
        return {

        }
    },
    props: {
        // 父组件courseIntroduce.vue传递过来的数据

    }
}
</script>

<style lang="scss" scoped>
.course_jieshao_box {
    display: flex;
    box-sizing: box;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;

    // image {
    //     width: 100%;
    // }

    video {
        width: 750rpx;
        height: 560rpx;
        margin-top: 20rpx;
    }
}
</style>