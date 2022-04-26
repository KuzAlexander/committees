<template>
  <div class="flex flex-col h-screen">
    <app-header :list="show"></app-header>
    <app-login class="grow" @show-block="showBlock"></app-login>
    <app-content class="grow" :content="show"></app-content>    
  </div>
</template>

<script>
import AppHeader from "@/components/AppHeader.vue";
import AppLogin from "@/components/AppLogin.vue";
import AppContent from "@/components/AppContent.vue";
export default {
  name: 'App',
  data() {
    return {
      show: false,
    }
  },
  methods: {
    showBlock() {
      this.show = true;
    }
  },
  components: {
    AppLogin,
    AppHeader,
    AppContent,
  }
}
</script>

<style>

</style>
