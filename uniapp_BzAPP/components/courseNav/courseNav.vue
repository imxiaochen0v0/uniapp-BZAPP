<template>
    <view class="course_nav_con">

        <view class="course_nav_info" v-for="(item, index) in  list " :key="index"
            @click="courseItemHandle(item.id, item.course)">
            <text class="course_nav_icon icon iconfont" :class="item.icon"></text>
            <view class="course_info_text">{{ item.text }}</view>
        </view>

    </view>
</template>

<script>
export default {
    data() {
        return {
            list: []
        }
    },
    methods: {
        courseItemHandle(id, course) {
            uni.navigateTo({
                url: '/pages/course/courseIntroduce/courseIntroduce?id=' + id + '&course=' + course
            })
        }
    },
    mounted() {
        uni.request({
            url: 'https://yapi.pro/mock/120455/nav',
            success: (res) => {
                this.list = res.data.data;
            },
        })
    },
}
</script>

<style lang="scss">
@import '@/common/font/iconfont.css';

.course_nav_con {
    display: flex;
    // 盒子模型不撑开容器本身大小
    box-sizing: border-box;
    flex-direction: row;
    flex-wrap: wrap;
    padding: 30rpx 25rpx;

    .course_nav_info {
        width: 20%;
        flex-direction: row;
        flex-wrap: wrap;
        text-align: center;
        margin-bottom: 30rpx;

        .course_nav_icon {
            font-size: 50rpx;
        }

        .icon-java,
        .icon-rengongzhineng,
        .icon-weifuwu {
            color: red;
        }

        .icon-h {
            color: #e44d26;

        }

        .icon-dashuju,
        .icon-zuzhijiagou,
        .icon-bianchengshibaobiao_icon {
            color: cornflowerblue;
        }

        .icon-ruanjianceshi,
        .icon-jianmo {
            color: darkseagreen;
        }


        .icon-huatong {
            color: gold;
        }

        .icon-icon-- {
            color: darksalmon;
        }

        .icon-chuangye {
            color: pink;
        }

        .course_info_text {
            width: 100%;
            font-size: 25rpx;
            margin-top: 20rpx;
            white-space: nowrap;
            text-overflow: ellipsis;
            overflow: hidden;
        }
    }
}
</style>