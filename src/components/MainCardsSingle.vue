<script setup>
  import { ref } from 'vue'
  import { faker } from '@faker-js/faker'

  import useAPI from '@/composables/useAPI'
   const { getDepartment } = useAPI()

  const fullName = faker.name.fullName()
  
  const selectCard = () => {
    console.log(`${props.employee.name} selected`)
  }

  const props = defineProps({
    employee: {
      type: Object,
      required: true,
      default: () => {
        return {
          employeeId:'123',
          name:'John Doe',
          email:'john.doe@example.com',
          title:'Position',
          departmentId:'123',
          quote:'Really Cool Quote',
          createdAt:'2022-01-01',
          updatedAt:'2022-01-01',
        }
      },
    },
  })

  const departmentResponse = await getDepartment(props.employee.departmentId)
  const department = ref(departmentResponse)
</script>

<template>
  <div class="card" @click="selectCard">
    <div class="card-image">
      <img :src="faker.internet.avatar()" alt="" srcset="" />
    </div>
    <div class="card-details">
      <p class="card-details-name"> {{ props.employee.name }} </p>
      <p class="card-details-job">{{ props.employee.title }} , {{ department.name }}</p>
      <p class="card-details-email">{{ props.employee.email }}</p>
      <p class="card-details-quote">"{{ props.employee.quote }}"</p>
    </div>
  </div>
</template>

<style scoped lang="postcss">
  .card {
    @apply cursor-pointer overflow-hidden rounded-2xl border bg-slate-100 p-8 shadow-md transition-transform duration-300 hover:scale-110 hover:shadow-xl hover:shadow-slate-900;

    &-image {
      img {
        @apply mx-auto rounded-2xl object-contain;
      }
    }

    &-details {
      @apply flex flex-col gap-4 pt-6 text-center;

      &-name {
        @apply -mt-4 text-3xl font-semibold tracking-wide text-slate-800 underline;
      }

      &-job {
        @apply -mt-4 text-xs text-yellow-700;
      }

      &-email {
        @apply font-semibold text-slate-700;
      }

      &-quote {
        @apply mt-4 font-semibold italic text-slate-500;
      }
    }
  }
</style>
