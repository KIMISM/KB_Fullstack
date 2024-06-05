<template>
  <div class="row">
    <div class="col p-3">
      <h2>할일 수정</h2>
    </div>
  </div>
  <div class="row">
    <div class="col">
      <div class="form-group">
        <!-- 요소의 id값과 연결해준다 -->
        <label htmlFor="todo">할일 :</label>
        <input
          type="text"
          class="form-control"
          id="todo"
          v-model="todoItem.todo"
        />
      </div>
      <div class="form-group">
        <label htmlFor="desc">설명 :</label>
        <textarea
          class="form-control"
          rows="3"
          id="desc"
          v-model="todoItem.desc"
        ></textarea>
      </div>
      <div class="form-group">
        <label htmlFor="done">완료여부:</label>&nbsp;
        <input type="checkbox" v-model="todoItem.done" />
      </div>
      <div class="form-group">
        <!-- 추가 버튼 클릭 시  -->
        <button
          type="button"
          class="btn btn-primary m-1"
          @click="updateTodoHandler"
        >
          수정
        </button>
        <!-- 취소 버튼 클릭 시  -->
        <button
          type="button"
          class="btn btn-primary m-1"
          @click="router.push('/todos')"
        >
          취소
        </button>
      </div>
    </div>
  </div>
</template>
<script setup>
import { inject, reactive } from 'vue';
import { useRouter, useRoute } from 'vue-router';
const todoList = inject('todoList');
const { updateTodo } = inject('actions');
const router = useRouter();
const currentRoute = useRoute();

const matchedTodoItem = todoList.value.find(
  (item) => item.id === currentRoute.params.id
);
if (!matchedTodoItem) {
  router.push('/todos');
}
const todoItem = reactive({ ...matchedTodoItem });
const updateTodoHandler = () => {
  let { todo } = todoItem;
  // 아이템의 할일 값이 비어있으면 경고창 출력
  if (!todo || todo.trim() === '') {
    alert('할일은 반드시 입력해야 합니다');
    // return을 만나면 함수 종료
    return;
  }
  // 넣어준 정보를 가지고 목록의 맨 뒤에 추가해줌
  updateTodo({ ...todoItem }, () => {
    // 업데이트한 후 전체 목록으로 돌아가기
    router.push('/todos');
  });
};
</script>
