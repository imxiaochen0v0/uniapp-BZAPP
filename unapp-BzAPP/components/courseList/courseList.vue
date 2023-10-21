<template>
    <view class="course_list_box">

        <view class="course_list_con">
            <view class="course_list_info" v-for="(item, index) in videoList" :key="index" @tap="tapVideo">
                <view class="course_list_info_txt">{{ item.type_name }}</view>

            </view>
        </view>

    </view>
</template>

<script>
export default {
    data() {
        return {

        }
    },
    methods: {
        tapVideo() {
            uni.navigateTo({
                url: '/pages/course/video/video'
            })
        }
    },
    props: {
        // 父组件courseIntroduce.vue传递过来的数据
        videoList: {
            type: Array,
            default: () => {
                return [];
            }
        },
    }
}
</script>

<style lang="scss" scoped>
.course_list_box {
    display: flex;
    box-sizing: border-box;
    flex-direction: column;
    width: 100%;
    padding: 0 15px;

    .course_list_con {
        display: flex;
        box-sizing: border-box;
        flex-direction: column;
        flex-grow: 1;

        .course_list_info {
            display: flex;
            box-sizing: border-box;
            flex-direction: center;
            overflow: hidden;
            flex: 1;
            width: 100%;
            height: 45px;
            line-height: 45px;
            font-size: 14px;
            border-bottom: 1px solid #efefef;

            .course_list_info_txt {
                white-space: nowrap;
                overflow: hidden;
                text-overflow: ellipsis;
            }
        }
    }
}
</style>