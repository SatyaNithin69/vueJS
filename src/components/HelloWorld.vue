<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    {{test}}
    <input v-model="test" @blur="addTodo">
    <button @click="addTodo">Add</button>
    <div v-for="task in tasks">{{task | capitalize | plural }}</div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  data() {
    return {
      test: "",
      tasks: ["commit", "push", "raise PR"]
    };
  },
  methods: {
    addTodo: function() {
      this.tasks.push(this.test);
      this.test = "";
    }
  },
  created: function() {
    console.log("created");
  },
  mounted: function() {
    console.log("mounted");
  },
  updated: function() {
    console.log("updated"); // when state changes
  },
  filters: {
    capitalize: function(value) {
      return value.toUpperCase();
    },
    plural: function(value) {
      return (value += "S");
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
