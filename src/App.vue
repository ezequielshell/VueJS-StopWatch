<template>
  <div>
    <div class="title">
      <h1 class="logoTitle">S</h1>
      <h1>StopWatch</h1>
    </div>
    <Display />
  </div>
</template>

<script>
import Display from "./components/Display.vue";

export default {
  components: { Display },
};
</script>

<style>
@font-face {
  font-family: "Montserrat-Regular";
  src: url("./assets/fonts/Montserrat-Regular.ttf");
}
@font-face {
  font-family: "Montserrat-Light";
  src: url("./assets/fonts/Montserrat-Light.ttf");
}
@font-face {
  font-family: "Montserrat-Thin";
  src: url("./assets/fonts/Montserrat-Thin.ttf");
}

* {
  padding: 0;
  margin: 0;
  background-color: #041f1e;
}

#app {
  font-family: "Montserrat-Regular";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}

.title {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 90px;
  color: #fff;
}

.logoTitle {
  background-color: #519872;
  color: #fff;
  margin-right: 10px;
  padding: 5px 15px;
  border-radius: 10px;
}
</style>
