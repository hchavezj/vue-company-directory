<script setup>
  import { ref } from 'vue'
  const brand = ref('🥡 The Fake Box Company Directory')
</script>

<template>
  <nav>
    <div class="wrapper">
      <div class="brand">
        <span class="brand-title">{{ brand }}</span>
      </div>
      <div class="menu">
        <a href="#" class="menu-item">Main</a>
        <a href="#" class="menu-item">About Us</a>
        <a href="#" class="menu-login">Logout</a>
      </div>
    </div>
  </nav>
</template>

<style scoped lang="postcss">
  nav {
    @apply flex h-20 bg-gray-800 text-gray-200;

    .wrapper {
      @apply container mx-auto flex w-full items-center justify-between;

      .brand {
        &-title {
          @apply border p-2 text-2xl font-bold text-white;
        }
      }

      .menu {
        @apply flex gap-2;

        &-item {
          @apply rounded-md px-4 py-2 hover:bg-emerald-500 hover:text-slate-900;
        }

        &-login {
          @apply rounded-md bg-red-500 px-4 py-2 text-black hover:bg-red-700;
        }
      }
    }
  }
</style>
