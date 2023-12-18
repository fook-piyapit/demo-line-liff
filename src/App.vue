<script setup lang="ts">
import liff from "@line/liff";
import { watchEffect } from "vue";
import HelloWorld from "./components/HelloWorld.vue";

const initializeLIFF = async () => {
  const liffId = ""; // Adding LIFF ID HERE

  try {
    await liff.init({ liffId: liffId }); // try comment this line #2
    // You will see error NEED TO CALL LIFF INIT

    // also try comment this if #3
    if (!liff.isLoggedIn()) {
      return liff.login({ redirectUri: window.location.href });
    }
    // You will see error NEED  LIFF ID NOT FOUND (because liff is not initialize)

    console.log(await liff.getProfile()) // LOG LINE USER DATA

  } catch (error) {
    console.error(error);
  }
};

watchEffect(async () => {
  // await initializeLIFF(); // try comment this line #1
});
</script>

<template>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <HelloWorld msg="Vite + Vue" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
