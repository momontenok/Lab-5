<template>
  <div id="app">
    <h1>Пользователи</h1>

    <div v-for="user in users" :key="user.login.uuid">
      <img :src="user.picture.medium" alt="user photo" />
      <div>
        {{ user.name.first }} {{ user.name.last }}, {{ user.dob.age }} лет
      </div>
      <div class="phone">{{ user.phone }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {},

  data() {
    return {
      users: [],
    };
  },

  mounted() {
    fetch('https://randomuser.me/api/?results=10')
      .then((data) => data.json())
      .then((data) => {
        this.users = data.results;
      });
  },
};
</script>

<style>
.phone {
  margin-bottom: 15px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
