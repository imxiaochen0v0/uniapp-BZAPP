<template>
  <view class="home">

    <view class="courseIntroduce_box">
      <view class="courseIntroduce_des">
        <view class="courseIntroduce_info">{{ introduce }}</view>
      </view>

      <CourseIntroduceData :msg="introduceList" />

      <view class="question_line"></view>

      <view class="courseIntroduce_tab_box">
        <view class="courseIntroduce_tab_nav">
          <view :class="{ btna: count === index }" v-for="(item, index) in items" :key="index" @tap="change(index)">{{
            item }}
          </view>
        </view>
        <view class="courseIntroduce_tab_con">
          <view class="discount_info" :class="{ dis: count === 0 }">
            <CourseList :videoList="Clist" />
          </view>
          <view class="discount_info" :class="{ dis: count === 1 }">
            <CourseDescribes :images="ImageT" />
          </view>
        </view>
      </view>
    </view>

  </view>
</template>

<script>
import CourseIntroduceData from '../../../components/courseIntroduceData/courseIntroduceData.vue'
import CourseList from '../../../components/courseList/courseList.vue'
import CourseDescribes from '../../../components/courseDescribes/courseDescribes.vue'
export default {
  data() {
    return {
      introduce: "",
      introduceList: [],
      items: ["课程章节", "课程介绍"],
      count: 0,
      Clist: [],
      ImageT: [],
    }
  },
  methods: {
    change(index) {
      this.count = index
    }
  },
  onLoad(options) {
    uni.request({
      url: 'https://www.itbaizhan.cn/api/course/detail',
      data: {
        id: options.id,
        course: options.course
      },
      success: (success) => {
        this.introduce = success.data.data.introduce
        this.introduceList = success.data.data.introduceList
        this.Clist = success.data.data.Clist
        this.ImageT = success.data.data.image
      },
    })
  },
  components: {
    CourseIntroduceData,
    CourseList,
    CourseDescribes
  }
}
</script>

<style lang="scss" scoped>
.courseIntroduce_box {
  display: flex;
  box-sizing: box;
  flex-direction: column;
  margin-bottom: 90px;

  .courseIntroduce_des {
    display: flex;
    box-sizing: border-box;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    background-color: #FFC0CB;
    padding: 0 10px 15px;
    overflow: hidden;

    .courseIntroduce_info {
      display: flex;
      box-sizing: box;
      width: 100%;
      color: #fff;
      font-size: 16px;
      line-height: 24px;
    }
  }

  //tab
  .courseIntroduce_tab_box {
    display: flex;
    box-sizing: border-box;
    flex-direction: column;

    .courseIntroduce_tab_nav {
      display: flex;
      box-sizing: border-box;
      flex-direction: row;
      background-color: #fff;
      border-bottom: 1px solid #e4e4e4;
      margin-bottom: 20px;

      view {
        height: 50px;
        line-height: 50px;
        font-size: 16px;
        flex-grow: 1;
        text-align: center;
        background-color: #fff;

      }
    }

    .discount_info {
      display: none;
    }

    .btna {
      display: flex;
      box-sizing: border-box;
      justify-content: center; //水平方向对齐
      color: #FFC0CB;
      position: relative;
    }

    .btna::after {
      content: '';
      width: 40px;
      height: 3px;
      background-color: #FFC0CB;
      position: absolute;
      bottom: 0;
      left: 50%;
      margin-left: -20px;
    }

    .dis {
      display: block;
    }
  }
}
</style>