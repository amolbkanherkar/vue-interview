<template>
  <h1>Dynamic Nav Builder change</h1>
  <p>You can use these arrow characters: ▼ ▶ •</p>
  <dynamic-nav :navItems="navItems"></dynamic-nav>
</template>

<script>
import DynamicNav from './components/DynamicNav.vue';
import { fetchData } from './navData.js';

export default {
  name: 'App',
  components: {
    DynamicNav,
  },
  data() {
    return {
      navItems: [],
    };
  },
  methods: {
    async setNavData() {
      try {
        this.navItems = await fetchData();
      } catch (error) {
        console.log('Error while getting nav data : ', error);
      }
    },
  },
  created() {
    this.setNavData();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
