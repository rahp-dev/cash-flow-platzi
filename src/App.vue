<template>
  <Suspense>
    <template #default>
      <HomeView />
    </template>
    <template #fallback>
      <SplashScreen />
    </template>
  </Suspense>
</template>

<script>
import { defineAsyncComponent } from "vue";

import "./assets/tailwind.css";
import SplashScreen from "./components/SplashScreen.vue";

export default {
  components: {
    HomeView: defineAsyncComponent(
      () =>
        new Promise((resolve) => {
          setTimeout(() => {
            resolve(import("@/components/HomeView.vue"));
          }, 2500);
        })
    ),
    SplashScreen,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap");

html,
body,
.app {
  min-height: 100vh;
  margin: 0;
  font-family: "Roboto", sans-serif;
}
</style>
