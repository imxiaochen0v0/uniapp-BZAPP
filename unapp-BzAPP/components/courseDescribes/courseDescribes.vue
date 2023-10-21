<template>
    <view class="course_jieshao_box">
        <!-- <image src="" mode="widthFix" /> -->
        <text class="text">404</text>
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

    image {
        width: 100%;
    }

    .text {
        font-size: 100rpx;
        font-weight: 700;
        color: pink;
        margin-top: 100rpx;
    }
}
</style>