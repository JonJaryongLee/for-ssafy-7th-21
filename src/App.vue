<template>
  <div id="app">
    <header>
      <Header />
    </header>
    <main>
      <div
        class="each-student-container"
        v-for="(student, index) in students"
        v-bind:key="index"
      >
        <img v-bind:src="student.img" alt="학생사진" />
        <div class="student-name">{{ student.name }}</div>
      </div>
    </main>
    <footer>
      <Footer />
    </footer>
  </div>
</template>

<script>
import axios from "axios";

import Header from "./components/Header";
import Footer from "./components/Footer";

export default {
  name: "App",
  components: {
    Header,
    Footer,
  },
  data() {
    return {
      students: [],
    };
  },
  async created() {
    const response = await axios.get("/name.json");
    this.students = response.data;
  },
};
</script>

<style>
#app {
  font-family: "Nanum Gothic", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  height: 100vh;
  display: flex;
  flex-direction: column;
}

header {
  flex: 2;
  display: flex;
  align-items: center;
  justify-content: center;
  padding-top: 20px;
}

main {
  flex: 5;
  display: flex;
  flex-direction: column;
  /* overflow: scroll; */
  justify-content: center;
  margin-top: 20px;
}

footer {
  flex: 1;
}

header .header h1 {
  font-weight: bold;
}

footer .footer div {
  margin-left: 10px;
  margin-top: 10px;
}

.each-student-container {
  margin-left: 50px;
  margin-right: 50px;
  margin-bottom: 30px;
  display: flex;
}

img {
  width: 120px;
  height: 120px;
}

.student-name {
  font-weight: bold;
  padding-top: 10px;
  padding-left: 10px;
}
</style>
