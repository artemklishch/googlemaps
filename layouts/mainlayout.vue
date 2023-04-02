<template>
  <b-container :class="$style.MainLayout" fluid>
    <NavMobile v-if="isMobile" :navRoutes="navRoutes" />
    <NavDesctop v-else :navRoutes="navRoutes" />
    <b-container class="p-2 flex-grow-1 d-flex flex-column m-0" fluid>
      <Nuxt />
    </b-container>
    <Footer />
  </b-container>
</template>

<script>
import NavMobile from "~/components/NavMobile";
import Footer from "~/components/Footer";
import NavDesctop from "~/components/NavDesctop";

export default {
  name: "MainLayout",
  components: { NavMobile, Footer, NavDesctop },
  data() {
    return {
      navRoutes: [
        { path: "/", label: "Home Page" },
        { path: "/mappage", label: "Map Page" },
        { path: "/placespage", label: "Places Page" },
      ],
      isMobile: true,
    };
  },
  mounted() {
    this.setIsMobileView();
    window.addEventListener("resize", this.setIsMobileView);
  },
  destroyed() {
    window.removeEventListener("resize", this.setIsMobileView);
  },
  methods: {
    setIsMobileView() {
      const width = window.innerWidth;
      if (width >= 720 && this.isMobile !== false) {
        this.isMobile = false;
      } else if (width < 720 && this.isMobile !== true) {
        this.isMobile = true;
      }
    },
  },
};
</script>

<style lang="scss" scoped module src="./MainLayout.module.scss" />
