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
  user_store.createUser(user_input.value)

  user_input.value = {
    name: '',
    email: '',
  }
}
</script>

<template>
  Hello, World!
</template>

<style>

</style>
