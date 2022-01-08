<template>
  <b-navbar centered>
    <template #start>
      <template v-for="(menu, i) in listMenuProp">
        <b-navbar-item :key="i" class="menu-title-box" href="#">
          <p v-if="menu.display">{{ menu.title }}</p>
        </b-navbar-item>
      </template>
    </template>
  </b-navbar>
</template>

<script>
export default {
  name: "MenuNavbarComponent",
  props: {
    listMenuProp: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="scss">
.menu-title-box {
  font-weight: bold;
  font-size: 12px;
}
</style>