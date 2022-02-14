<template>
  <div class="home">
    <!-- <HelloWorld /> -->
    <!-- <h1>Home</h1> -->
    <v-container>
      <TodoAdd @onSubmit="addTask" />
      <TodoList @onRemove="removeTask" :todos="todos | reversed" />
      <!-- <TodoList @onRemove="removeTask" :todos="reversedTodo" /> -->
      <v-row class="d-flex flex-row justify-center align-center">
        <img
          class="mt-10"
          contain
          width="100"
          height="100"
          src="../assets/test.png"
        />
      </v-row>
    </v-container>
  </div>
</template>

<script>
// import HelloWorld from "../components/HelloWorld";
import TodoList from "../components/TodoList.vue";
import TodoAdd from "../components/TodoAdd.vue";
import axios from "axios";
export default {
  name: "home",
  computed: {
    reversedTodo() {
      return this.todos.slice().reverse(); //#1
    },
  },
  filters: {
    reversed(value) {
      return value.slice().reverse(); //#2
    },
  },
  components: {
    // HelloWorld,
    TodoList,
    TodoAdd,
  },
  async mounted() {
    let result = await axios.get("https://jsonplaceholder.typicode.com/todos");
    this.todos = result.data;
  },
  methods: {
    async addTask(task) {
      let result = await axios.post(
        "https://jsonplaceholder.typicode.com/todos",
        task
      );
      // alert(JSON.stringify(result.data))
      this.todos.push(result.data);
    },
    removeTask(id) {
      axios
        .delete("https://jsonplaceholder.typicode.com/todos/" + id)
        .then(result => {
           alert(JSON.stringify(result.data));
          // console.log(JSON.stringify(result.data))
          this.todos = this.todos.filter(item => item.id !== id);
        })
        .catch(error => {
          console.log(error);
        });
        //  .catch(error => {
        //     alert(error);
        // });
    },
  },
  data() {
    return {
      todos: [],
      todos_mockup: [
        { id: 1, title: "Task 1", completed: false },
        { id: 2, title: "Task 2", completed: true },
        { id: 3, title: "Task 3", completed: false },
        { id: 4, title: "Task 4", completed: true },
      ],
    };
  },
};
</script>
