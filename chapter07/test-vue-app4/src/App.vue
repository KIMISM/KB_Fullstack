<script>
//지역 컴포넌트 등록 방법(사용할 파일에서만 명시)
import CheckboxItem from './components/CheckboxItem.vue';
export default {
  name: 'App',
  components: { CheckboxItem },
  data() {
    return {
      //idols를 객체 배열로 만들어줌
      //props 부분에서 checked의 기본값을 false로 정해줬기 때문에 생략 가능
      idols: [
        { id: 1, name: 'WINNER', checked: true },
        { id: 2, name: 'Black Pink', checked: false },
        { id: 3, name: 'EXO', checked: false },
        { id: 4, name: 'ITZY', checked: false },
      ],
    };
  },
};
</script>
<template>
  <div>
    <h2>관심있는 K-POP 가수?</h2>
    <hr />
    <ul>
      <!-- :idol은 자식한테 props로 전달해주는 속성(사용자 정의) -->
      <!-- idol은 idols 배열을 돌면서 객체 하나씩 접근 -->
      <CheckboxItem v-for="idol in idols" :key="idol.id" :idol="idol" />
    </ul>
  </div>
</template>
