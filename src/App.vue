<template>
  <div>
    <Header />
    <div class="wrapper">
      <UsersView />
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import UsersView from './components/UsersView.vue';

export default {
  name: 'App',
  components: {
    Header,
    UsersView,
  }
}
</script>

<style>
#app {
  font-family: "Roboto";
  font-style: normal;
  font-weight: 400;
  color: #696969;
}

.wrapper {
  position: absolute;
  left: 0;
  top: 77px;
  width: 100%;
  height: 100%;
  padding: 30px 60px;
}
</style>
