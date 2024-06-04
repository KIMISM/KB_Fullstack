<script>
import InputName from './components/InputName.vue';
export default {
  name: 'App',
  components: { InputName },
  data() {
    return {
      searchName: 'John',
    };
  },
  methods: {
    changeSearchName(name) {
      console.log(name);
      this.searchName = name;
      // 선택된 탭을 업데이트
      this.currentTab = tab;
    },
  },
};
</script>

<template>
  <div>
    <!-- 자식의 name을 searchName으로 전달하고 다시 자식의 변경값을 받아옴 -->
    <!-- <InputName :name="searchName" @update:name="changeSearchName"/>아래 코드로 생략 가능 -->
    <InputName v-model:name="searchName" />
    <h3>검색어:{{ searchName }}</h3>
  </div>
</template>
