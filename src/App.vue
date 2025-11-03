<script setup>
import { ref, computed, watch } from 'vue';

const newTitle = ref('');
const filter = ref('all'); // all | active | completed
const todos = ref(load() ?? []);

function load() {
  try {
    return JSON.parse(localStorage.getItem('todos-v1') || '[]');
  } catch {
    return [];
  }
}
watch(todos, (v) => localStorage.setItem('todos-v1', JSON.stringify(v)), { deep: true });

function addTodo() {
  const title = newTitle.value.trim();
  if (!title) return;
  todos.value.unshift({ id: crypto.randomUUID(), title, done: false, editing: false });
  newTitle.value = '';
}
function toggle(id) {
  const t = todos.value.find((t) => t.id === id);
  if (t) t.done = !t.done;
}
function remove(id) {
  todos.value = todos.value.filter((t) => t.id !== id);
}
function clearCompleted() {
  todos.value = todos.value.filter((t) => !t.done);
}
function startEdit(t) {
  t.editing = true;
  t._backup = t.title;
}
function finishEdit(t) {
  t.editing = false;
  t.title = t.title.trim();
  if (!t.title) remove(t.id);
  delete t._backup;
}
function cancelEdit(t) {
  t.editing = false;
  t.title = t._backup;
  delete t._backup;
}

const remaining = computed(() => todos.value.filter((t) => !t.done).length);
const filtered = computed(() => {
  if (filter.value === 'active') return todos.value.filter((t) => !t.done);
  if (filter.value === 'completed') return todos.value.filter((t) => t.done);
  return todos.value;
});
</script>

<style>
.app button {
  padding: 6px 10px;
  border: 1px solid #ddd;
  background: #fafafa;
  border-radius: 6px;
  cursor: pointer;
}
.app button.active {
  border-color: #333;
}
</style>

<template>
  <div
    class="app"
    style="
      max-width: 560px;
      margin: 48px auto;
      padding: 24px;
      border: 1px solid #eee;
      border-radius: 16px;
    "
  >
    <h1 style="margin: 0 0 16px">Vue Todo</h1>

    <form @submit.prevent="addTodo" style="display: flex; gap: 8px">
      <input
        v-model="newTitle"
        placeholder="할 일을 입력하고 Enter"
        style="flex: 1; padding: 10px; border: 1px solid #ddd; border-radius: 8px"
      />
      <button
        type="submit"
        style="
          padding: 10px 14px;
          border: 0;
          background: #2ecc71;
          color: #fff;
          border-radius: 8px;
          cursor: pointer;
        "
      >
        추가
      </button>
    </form>

    <div style="display: flex; gap: 8px; margin: 14px 0">
      <button :class="{ active: filter === 'all' }" @click="filter = 'all'">전체</button>
      <button :class="{ active: filter === 'active' }" @click="filter = 'active'">진행중</button>
      <button :class="{ active: filter === 'completed' }" @click="filter = 'completed'">
        완료
      </button>
    </div>

    <ul
      style="
        list-style: none;
        padding: 0;
        margin: 0;
        display: flex;
        flex-direction: column;
        gap: 8px;
      "
    >
      <li
        v-for="t in filtered"
        :key="t.id"
        style="
          display: flex;
          align-items: center;
          gap: 8px;
          border: 1px solid #eee;
          padding: 10px;
          border-radius: 8px;
        "
      >
        <input type="checkbox" :checked="t.done" @change="toggle(t.id)" />
        <template v-if="!t.editing">
          <span :style="{ textDecoration: t.done ? 'line-through' : 'none', flex: 1 }">{{
            t.title
          }}</span>
          <button @click="startEdit(t)">수정</button>
          <button @click="remove(t.id)">삭제</button>
        </template>
        <template v-else>
          <input
            v-model="t.title"
            @keyup.enter="finishEdit(t)"
            @keyup.esc="cancelEdit(t)"
            style="flex: 1; padding: 6px; border: 1px solid #ddd; border-radius: 6px"
          />
          <button @click="finishEdit(t)">확인</button>
          <button @click="cancelEdit(t)">취소</button>
        </template>
      </li>
    </ul>

    <div
      style="display: flex; justify-content: space-between; align-items: center; margin-top: 14px"
    >
      <small>남은 일: {{ remaining }}개</small>
      <button @click="clearCompleted">완료 모두 지우기</button>
    </div>
  </div>
</template>
