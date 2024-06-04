<!-- <script setup>
import { RouterLink, RouterView } from 'vue-router';
import HelloWorld from './components/HelloWorld.vue';
</script> -->

<template>
  <div class="container">
    <!-- Header처럼 변하지 않고 고정된 부분은 components 폴데어 생성 -->
    <Header />
    <!-- router-view처럼 동적으로 변하는 페이지들은 pages폴더에 생성 -->
    <router-view></router-view>
  </div>
</template>
<script>
import Header from '@/components/Header.vue';
export default {
  // 콤마 잊지 말자
  name: 'App2',
  components: { Header },
};
</script>
<style>
.container {
  text-align: center;
  margin-top: 10px;
}
</style>
