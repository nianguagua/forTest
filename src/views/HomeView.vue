<template>
  <main>
    <!-- <div class="box1">15rem</div>
    <div class="box2">15px</div>
    <el-button type="primary">Primary</el-button> -->

    <el-skeleton animated :loading="loading" :count="3">
      <template #template>
        <div class="skeleton-box">
          <el-skeleton-item class="skeleton-box-image" variant="image" />
          <div class="skeleton-content">
            <div class="left">
              <el-skeleton-item
                class="skeleton-content-circle"
                variant="circle"
              />
            </div>
            <div class="right">
              <el-skeleton-item class="skeleton-content-p" variant="p" />
              <el-skeleton-item class="skeleton-content-p" variant="p" />
              <el-skeleton-item class="skeleton-content-p" variant="p" />
              <el-skeleton-item class="skeleton-content-p" variant="p" />
            </div>
          </div>
        </div>
      </template>
      <template #default>
        <div v-for="t in personList" :key="t.id" class="skeleton-box">
          <div class="skeleton-box-image">
            <img :src="t.img" alt="" />
          </div>
          <div class="skeleton-content">
            <div class="left">
              <img :src="t.face" class="skeleton-content-circle" alt="" />
            </div>
            <div class="right">
              <p class="skeleton-content-p">
                姓名: <span>{{ t.name }}</span>
              </p>
              <p class="skeleton-content-p">
                职业: <span>{{ t.job }}</span>
              </p>
              <p class="skeleton-content-p">
                LOVE: <span>{{ t.love }}</span>
              </p>
            </div>
          </div>
        </div>
      </template>
    </el-skeleton>
  </main>
</template>

<script setup>
import { onMounted, ref } from "vue";
import img1 from "@/assets/image/3.jpg";
import img2 from "@/assets/image/4.jpg";
import img3 from "@/assets/image/5.jpg";
import face1 from "@/assets/image/1.jpg";
import face2 from "@/assets/image/6.jpg";

const loading = ref(true);
const personList = ref([
  {
    id: 1,
    img: img1,
    face: face1,
    name: "黎深",
    job: "心外科医生",
    love: "长暇市天气晴朗，我想你应该一切都好",
  },
  {
    id: 2,
    img: img2,
    face: face1,
    name: "沈星回",
    job: "菲普斯王储",
    love: "就让星星自己落下来留在你身边吧",
  },
  {
    id: 3,
    img: img3,
    face: face2,
    name: "秦彻",
    job: "N109区长",
    love: "你好凶啊~",
  },
]);
onMounted(() => {
  setTimeout(() => {
    loading.value = false;
  }, 1000);
});
</script>

<style lang="scss" scoped>
.skeleton-box {
  width: 2.6rem;
  height: 3.6rem;
  border: 1px solid #dadada;
  box-shadow: 5px 5px 6px #e4e4e4;
  border-radius: 5px;
  float: left;
  margin-right: 10px;
  .skeleton-box-image {
    width: 100%;
    height: 2.6rem;
    img {
      width: 100%;
      height: 100%;
    }
  }
  .skeleton-content {
    padding: 15px 5px;
    // margin-top: 10px;
    display: flex;
    justify-content: space-between;
    .left,
    .right {
      // height: 0.6rem;
      display: flex;
      // border: 1px solid red;
    }
    .left {
      width: 0.6rem;
    }
    .right {
      flex: 1;
      padding-left: 8px;
      flex-direction: column;
    }
    .skeleton-content-circle {
      width: 0.6rem;
      height: 0.6rem;
      border-radius: 50%;
      // border: 1px solid #333;
    }
    .skeleton-content-p {
      font-size: 0.12rem;
      color: #666;
      // span {
      //   color: #999;
      // }
      &:not(:last-child) {
        margin-bottom: 5px;
      }
      &:first-child {
        width: 40%;
      }
      &:nth-child(2) {
        width: 80%;
      }
      &:nth-child(4) {
        width: 60%;
      }
      &.el-skeleton__item {
        height: 15px;
      }
    }
  }
}
</style>
