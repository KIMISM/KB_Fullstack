<template>
  <div>
    <!-- 체크박스 변경시 id값과 현재 체크박스의 체크상태값을 check-changed 이벤트에 담어서 
        부모로 보냄 -->
    <input
      type="checkbox"
      :value="id"
      :checked="checked"
      @change="$emit('check-changed', { id, checked: $event.target.checked })"
    />
    <!-- 체크박스가 체크됐을 경우 span태그 렌더링-->
    <!-- 보여질 경우 이탤릭체로 label 출력 -->
    <span
      v-if="checked === true"
      style="color: blue; text-decoration: underline"
    >
      <i>{{ label }}</i></span
    >
    <!-- 체크 해제됐을 경우 렌더링되는 span -->
    <span v-else style="color: gray">{{ label }}</span>
  </div>
</template>
<script>
export default {
  name: 'CheckBox1',
  props: ['id', 'checked', 'label'], //부모 컴포넌트로부터 받을 속성들
};
</script>
