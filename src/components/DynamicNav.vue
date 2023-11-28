<template>
  <ul v-if="navItems.length > 0">
    <li v-for="item in navItems" :key="item.id">
      <span @click="toggleNavItem(item)">
        <span
          v-if="item.children && item.children.length > 0"
          v-html="navItemIcon(item)"
          >▼</span
        >
        <span v-else>•</span>
        {{ item.name }}
      </span>
      <dynamic-nav v-if="item.isOpen" :navItems="item.children"></dynamic-nav>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'DynamicNav',
  props: {
    navItems: {
      type: Array,
      required: true,
    },
  },
  methods: {
    toggleNavItem(item) {
      item.isOpen = !item.isOpen;
    },
    navItemIcon(item) {
      return item.isOpen ? '▼' : '▶';
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
a {
  color: #42b983;
}
ul {
  list-style: none;
  padding-left: 10px;
}
</style>
