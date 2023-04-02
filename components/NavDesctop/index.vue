<template>
  <b-container :class="$style.NavDesctop" fluid>
    <NuxtLink :to="navRoutes[0].path">
      <b-img
        src="~/assets/images/globe-icon.svg"
        alt="Globe Icon"
        width="40"
        role="button"
        class="active-opacity"
      />
    </NuxtLink>
    <b-navbar :class="$style.NavDesctop__menu">
      <NuxtLink
        v-for="(route, index) in navRoutes"
        :key="index"
        :class="$style.NavDesctop__menu_link"
        :to="route.path"
      >
        {{ route.label }}
      </NuxtLink>
    </b-navbar>
  </b-container>
</template>

<script>
export default {
  name: "NavDesctop",
  props: {
    navRoutes: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style lang="scss" module src="./NavDesctop.module.scss" />
