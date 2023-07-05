<template>
  <router-view />
</template>

<script lang="ts">
import { getCurrentInstance, onMounted } from 'vue';

  //
  export default {
    setup() {
      const internalInstance = getCurrentInstance();
      const userData = {
          id: 101,
          handle: "biot",
      }
      const isLoggedIn = true;

      onMounted(() => {
        internalInstance!.appContext.config.globalProperties.$user = {
          userData,
          isLoggedIn
        };
      })
    }
  }
</script>
