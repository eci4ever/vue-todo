<template>
  <div id="app">
    <Header />
    <router-view />
  </div>
</template>

<script>
// import Todos from "./components/Todos";
// import AddTodo from "./components/AddTodo";
import Header from "./components/layout/Header";
//import { v4 as uuidv4 } from 'uuid';
// import axios from "axios";

export default {
  name: 'App',
  components: {
    Header,
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: white;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
