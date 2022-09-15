<script setup>
  import { faker } from '@faker-js/faker'
  const fullName = faker.name.fullName()
</script>

<template>
  <div class="card">
    <div class="card-image">
      <img :src="faker.internet.avatar()" />
    </div>
    <div class="card-details">
      <p class="card-details-name">
        {{ fullName }}
      </p>
      <p class="card-details-job">{{ faker.name.jobTitle() }} , {{ faker.name.jobArea() }}</p>
      <p class="card-details-email">{{ faker.internet.exampleEmail(fullname) }}</p>
      <p class="card-details-quote">"{{ faker.lorem.paragraph() }}"</p>
    </div>
  </div>
</template>

<style scoped lang="postcss">
  .card {
    @apply cursor-pointer overflow-hidden rounded-2xl bg-slate-100 p-8 shadow-md transition-transform duration-300 hover:scale-110 hover:shadow-xl hover:shadow-slate-900;
    &-image {
      img {
        @apply mx-auto rounded-full object-contain;
      }
    }
    &-details {
      @apply flex flex-col gap-4 pt-6 text-center;
      &-name {
        @apply text-3xl font-semibold tracking-wide text-slate-800 underline;
      }
      &-job {
        @apply -mt-4 text-xs text-yellow-700;
      }
      &-email {
        @apply text-slate-700;
      }
      &-quote {
        @apply font-semibold italic text-slate-500;
      }
    }
  }
</style>
