<template>
  <div>
    <!-- 체크박스 변경시 id값과 현재 체크박스의 체크상태값을 check-changed 이벤트에 담어서 
        부모로 보냄 -->
    <slot name="icon"></slot>
    <input
      type="checkbox"
      :value="id"
      :checked="checked"
      @change="$emit('check-changed', { id, checked: $event.target.checked })"
    />
    <!-- slot으로 부모에서 보낸 span을 전달받는다 -->
    <!-- 부모에서 온 데이터가 없을 경우 기본값인 'item'이 출력된다 -->
    <slot name="label">Item</slot>
  </div>
</template>
<script>
export default {
  name: 'CheckBox2',
  props: ['id', 'checked', 'label'], //부모 컴포넌트로부터 받을 속성들
};
</script>
