<template>
  <div>
    X: <input type="text" v-model.number="state.x" /> <br />
    Y:<input type="text" v-model="state.y" /><br />

    <div>결과 : {{ result }}</div>
  </div>
</template>

<script>
// composition API 내의 함수를 사용하려면import 필수
import { reactive, computed } from 'vue';
export default {
  name: 'Calc4',
  setup() {
    // conputed로 계산해주기 때문에 result초기화 필요 없어짐
    const state = reactive({ x: 10, y: 20 });
    const result = computed(() => {
      return state.x + state.y;
    });
    // return을 해줘야 template쪽에서 사용 가능
    return { state, result };
  },
};
</script>
