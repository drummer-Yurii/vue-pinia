<script setup>
import { ref } from 'vue';
import { useUserStore } from './stores/users';

const user_store = useUserStore();

const user_input = ref({
  name: '',
  email: '',
});

const sort = ref(false);

const CreateUser = () => {
  if (!user_input.value.name || !user_input.value.email) {
    return alert('Please enter both name and email')
  }
  user_store.create(user_input.value)

  user_input.value = {
    name: '',
    email: '',
  }
}
</script>

<template>
  <main>
    <h1>Team manager</h1>
    <form @submit.prevent="CreateUser">
      <input type="text" placeholder="e.g. Naruto Uzumaki" v-model="user_input.name" />
      <input type="email" placeholder="e.g. hokage@ninja.com" v-model="user_input.email" />
      <input type="submit" value="Create user">
    </form>

    <div class="users">
      <div v-for="user in user_store.users" :key="user" class="user">
        {{ user }}
      </div>
    </div>
  </main>
</template>

<style>

</style>
