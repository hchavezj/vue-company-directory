<script setup>
  import { ref } from 'vue'
  import { useAuth } from '@/composables/useAuth'

  const { isAuthenticated, logout, user } = useAuth()

  const brand = ref(import.meta.env.VITE_APP_NAME)
</script>

<template>
  <nav>
    <div class="wrapper">
      <RouterLink :to="{ name: 'Home' }" class="brand">
        <span class="brand-title">{{ brand }}</span>
      </RouterLink>
      <div class="menu">
        <p v-show="isAuthenticated" class="px-2 py-4">
          👤
          <RouterLink :to="{ name: 'Settings' }">
            <span class="hover:underline">
              <strong>[{{ user.name }}]</strong>
            </span>
          </RouterLink>
        </p>
        <div v-if="isAuthenticated">
          <RouterLink :to="{ name: 'Settings' }" href="#" class="menu-item">Settings</RouterLink>
          <button class="menu-logout" @click="logout">Logout</button>
        </div>
        <div v-else>
          <RouterLink :to="{ name: 'Login' }" href="#" class="menu-login">Login</RouterLink>
        </div>
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
        div {
          @apply py-2;
        }

        &-item {
          @apply rounded-md px-4 py-2 hover:bg-emerald-500 hover:text-slate-900;
        }

        &-login {
          @apply rounded-md bg-blue-500 px-4 py-2 text-black hover:bg-red-700;
        }

        &-logout {
          @apply mx-2 rounded-md bg-red-500 px-4 py-2 text-black hover:bg-red-700;
        }
      }
    }
  }
</style>
