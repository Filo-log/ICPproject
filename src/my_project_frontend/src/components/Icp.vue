<script setup>
import { ref } from 'vue';
import { my_project_backend } from 'declarations/my_project_backend/index';
let greeting = ref('');

async function handleSubmit(e) {
  e.preventDefault();
  const target = e.target;
  const name = target.querySelector('#name').value;
  await my_project_backend.greet(name).then((response) => {
    greeting.value = response;
  });
}
</script>

<template>
    <img src="/logo2.svg" alt="DFINITY logo" class="icp-img" />
    <form action="#" @submit="handleSubmit">
      <label for="name">Enter your name: &nbsp;</label>
      <input id="name" alt="Name" type="type" />
      <button type="submit">Click Me!</button>
      <header>
        <h1 id="greeting">{{ greeting }}</h1>
        <h2>Student</h2>
      </header>
    </form>
</template>