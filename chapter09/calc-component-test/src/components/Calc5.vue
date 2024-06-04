<template>
  <div>
    X: <input type="text" v-model.number="x" /> <br />
    결과 : {{ result }}
  </div>
</template>

<script>
// composition API 내의 함수를 사용하려면import 필수
import { watch, ref } from 'vue';
export default {
  name: 'Calc5',
  setup() {
    // conputed로 계산해주기 때문에 result초기화 필요 없어짐
    const x = ref(0);
    const result = ref(0);
    // 기존 옵션 API의 watch옵션과 동일한 역할
    //첫번째 인자: 감시하고 싶은 데이터(반응성 데이터)
    //두번째 인자: 현재 값과 전의 값을 받아서 실행할 함수
    watch(x, (current, old) => {
      console.log(`${old} ==> ${current}`);
      result.value = current * 2;
    });
    // return을 해줘야 template쪽에서 사용 가능
    return { x, result };
  },
};
</script>
