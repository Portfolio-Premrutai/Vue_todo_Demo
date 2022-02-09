<template>
  <div class="home">
    <!-- <HelloWorld /> -->
    <!-- <h1>Home</h1> -->
    <v-container>
      <v-row>
        <v-col cols="10">
          <v-text-field name="name" label="Task" id="id"></v-text-field>
        </v-col>
        <v-col cols="2">
          <v-btn block color="success">add</v-btn>
        </v-col>
      </v-row>

      <v-card>
        <v-card-title primary-title>
          <v-container>
            <v-row
              class="d-flex-row align-center"
              v-for="(item, index) in todos"
              :key="index"
            >
              <v-col cols="12" class="d-flex flex-row align-center">
                <v-checkbox v-model="value" value="value"></v-checkbox>
                <span>{{ item.title }}</span>
                <v-spacer></v-spacer>
                <v-btn color="error">x</v-btn>
              </v-col>
              <v-col cols="12">
                <v-divider></v-divider>
              </v-col>
            </v-row>
          </v-container>
        </v-card-title>
      </v-card>
    </v-container>
  </div>
</template>

<script>
// import HelloWorld from "../components/HelloWorld";

export default {
  name: "home",

  components: {
    // HelloWorld,
  },
  data() {
    return {
      todos: [
        { id: 1, title: "Task 1", completed: false },
        { id: 2, title: "Task 2", completed: true },
        { id: 3, title: "Task 3", completed: false },
        { id: 4, title: "Task 4", completed: true },
      ],
    };
  },
};
</script>
