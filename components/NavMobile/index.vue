<template>
  <b-container :class="$style.NavMobile" fluid>
    <b-row>
      <b-col class="d-flex align-center">
        <NuxtLink :to="navRoutes[0].path">
          <b-img
            src="~/assets/images/globe-icon.svg"
            alt="Globe Icon"
            width="40"
            role="button"
            class="active-opacity"
          />
        </NuxtLink>
      </b-col>
      <b-col class="d-flex justify-content-end align-center">
        <b-img
          src="~/assets/images/menu-icon.svg"
          alt="Menu Icon"
          width="40"
          role="button"
          class="active-opacity"
          @click="openMenu"
        />
      </b-col>
    </b-row>
    <b-navbar-nav :class="$style.NavMobile__menu" ref="navbarmenu">
      <b-img
        src="~/assets/images/close-icon-white.svg"
        alt="Close Icon"
        :class="$style.NavMobile__menu_close"
        @click="closeMenu"
      />
      <b-nav-text
        v-for="(route, index) in navRoutes"
        :key="index"
        :class="[
          $style.NavMobile__menu_link,
          $route.path === route.path ? $style.activeLink : '',
        ]"
        @click="onFollowLink(route.path)"
      >
        {{ route.label }}
      </b-nav-text>
    </b-navbar-nav>
  </b-container>
</template>

<script>
export default {
  name: "NavMobile",
  props: {
    navRoutes: {
      type: Array,
      required: true,
    },
  },
  methods: {
    openMenu() {
      this.$refs.navbarmenu.style.marginLeft = "0";
    },
    closeMenu() {
      this.$refs.navbarmenu.style.marginLeft = "-100%";
    },
    onFollowLink(page) {
      if (this.$route.path !== page) {
        this.$router.push(page);
      }
      this.closeMenu();
    },
  },
};
</script>

<style lang="scss" module src="./NavMobile.module.scss" />
