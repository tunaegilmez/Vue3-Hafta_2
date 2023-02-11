<template>
  <div class="container">
    <h3 class="text-center">Todo</h3>
    <hr class="my-2" />
    <AddSection :addNewTodo="addNewTodo" @add-todo="addNewTodo" />
    <ListSection />
    <!-- <TodoList @delete-todo-item="deleteItem" :myData="todoList" />
    <ResultBar :itemCount="todoList.length" /> -->
  </div>
</template>

<script>
import AddSection from "@/components/AddSection";
import ListSection from "@/components/ListSection";
// import TodoList from "@/components/TodoList";
// import ResultBar from "@/components/ResultBar";

export default {
  components: {
    AddSection,
    ListSection,
    // TodoList,
    // ResultBar,
  },
  created() {
    // setTimeout(() => {
    //   this.todoList = [
    //     { id: 1, text: "Todo Item #1" },
    //     { id: 2, text: "Todo Item #2" },
    //     { id: 3, text: "Todo Item #3" },
    //     { id: 4, text: "Todo Item #4" },
    //     { id: 5, text: "Todo Item #5" },
    //     { id: 6, text: "Todo Item #6" },
    //   ];
    // }, 2000);
  },
  data() {
    return {
      provideData: {
        todoList: [
          { id: 1, text: "Todo Item #1" },
          { id: 2, text: "Todo Item #2" },
          { id: 3, text: "Todo Item #3" },
          { id: 4, text: "Todo Item #4" },
          { id: 5, text: "Todo Item #5" },
          { id: 6, text: "Todo Item #6" },
        ],
      },
    };
  },
  provide() {
    return {
      provideData: this.provideData,
      deleteItem: this.deleteItem,
    };
  },
  methods: {
    testEvent(data) {
      alert(data);
    },
    deleteItem(todoItem) {
      this.provideData.todoList = this.provideData.todoList.filter((t) => t !== todoItem);
    },
    addNewTodo(todo) {
      this.provideData.todoList.push({
        id: new Date().getTime(),
        text: todo,
      });
    },
  },
};
</script>
