<template>
  <ul class="max-w-md mx-auto mt-10 p-4 border border-gray-300 rounded">
    <li
      v-for="item in items"
      :key="item.id"
      class="flex items-center gap-2 mb-2 border-b border-gray-200"
    >
      <slot v-bind="item"></slot>
    </li>
    <li>
      <slot name="footer" :all="all" :todo="todo" :done="done">
        All: {{ all }} | Todo: {{ todo }} | Done: {{ done }}
      </slot>
    </li>
  </ul>
</template>

<script lang="ts">
interface TodoItem {
  id: number;
  name: string;
  done: boolean;
}

export default {
  name: "TodoList",
  props: ["endpoint"],
  data: () => ({
    items: [] as TodoItem[],
    all: 3,
    todo: 1,
    done: 1,
  }),
  methods: {
    mockApi() {
      this.items = [
        { id: 1, name: "Todo 1", done: true },
        { id: 2, name: "Todo 2", done: true },
        { id: 3, name: "Todo 3", done: true },
      ];
    },
  },
  mounted() {
    setTimeout(() => {
      this.mockApi();
    }, 1000);
  },
};
</script>
