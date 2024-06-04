<script>
//지역 컴포넌트 등록 방법(사용할 파일에서만 명시)
import InputName from './components/InputName.vue';
export default {
  name: 'App',
  //components는 블록같은거
  components: { InputName },
  data() {
    return {
      parentName: '',
    };
  },
  methods: {
    nameChangedHandler(e) {
      //받아온 객체 안에 있는 name을 접근해서 data에 있는 parentName에 넣어줌
      this.parentName = e.name;
    },
  },
};
</script>
<template>
  <div>
    <!-- 자식 컴포넌트에서 정의한 nameChanged 이벤트를 nameChangedHandler 함수와 연결 -->
    <!-- (사용자 정의 이벤트) -->
    <InputName @nameChanged="nameChangedHandler" />
    <br />
    <h3>APP 데이터:{{ parentName }}</h3>
  </div>
</template>
