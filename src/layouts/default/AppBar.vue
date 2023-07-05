<template>
  <v-app-bar image="https://picsum.photos/1920/1080?random">
    <v-app-bar-title class="ml-5">
      <v-icon icon="mdi-circle-slice-3" />
      AISocMed
    </v-app-bar-title>
    
    <v-menu>
      <template v-slot:activator="{ props }">
        <v-avatar color="surface-variant" class="mr-3"></v-avatar>
        <v-list-item v-bind="props" v-if="isLoggedIn" class="text-white mr-5" :title="userData.handle"></v-list-item>
        <v-list-item v-bind="props" v-if="!isLoggedIn" class="text-white mr-5" title="Guest"></v-list-item>
      </template>
      <v-list>
        <v-list-item>
          <v-btn size="small" variant="plain">
            Your Posts
          </v-btn>
        </v-list-item>
        <v-list-item>
          <v-btn size="small" variant="plain">
            Logout
          </v-btn>
        </v-list-item>
      </v-list>
    </v-menu>
  </v-app-bar>
</template>

<script lang="ts">
import { getCurrentInstance } from 'vue';

  //
  export default {
    data() {
      const internalInstance = getCurrentInstance();
      return {
        userData: internalInstance?.appContext.config.globalProperties.$user.userData,
        isLoggedIn: internalInstance?.appContext.config.globalProperties.$user.isLoggedIn
      }
    }
  }
</script>
