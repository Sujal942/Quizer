<script setup>
import q from "./data/quizes.json";
import { ref, watch } from "vue";

const quizes = ref(q);
const search = ref();
watch(search, () => {
  quizes.value = q.filter((quizes) =>
    quizes.name.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>
<template>
  <div class="container">
    <header>
      <h1>Quizer</h1>
      <input v-model.trim="search" type="text" placeholder="Search..." />
    </header>
    <div class="card-container">
      <div v-for="quizes in quizes" :key="quizes.id" class="card">
        <img :src="quizes.img" alt="" />
        <div class="card-text">
          <h2>{{ quizes.name }}</h2>
          <span>{{ quizes.questions.length }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
header {
  display: flex;
  align-items: center;
  gap: 50px;
  justify-content: center;
}
header h1 {
  letter-spacing: 20px;
  margin-top: 50px;
}
header input {
  margin-top: 50px;
  width: 250px;
  height: 40px;
  padding: 10px 5px;
  font-size: medium;
  color: azure;
  border-radius: 5px;
  border: none;
  background-color: rgba(156, 150, 150, 0.284);
}
.card-container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  flex-wrap: wrap;
}
.card {
  margin: 30px 20px;
  border-radius: 20px;
  box-shadow: 1px 1px 10px rgba(245, 222, 179, 0.318);
  border: none;
  color: rgb(60, 53, 46);
  background-color: rgba(76, 81, 81, 0.392);
  width: 300px;
  height: 300px;
}
.card img {
  width: 100%;
  height: 200px;
  margin: 0%;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
}
.card-text {
  margin: 20px;
}
</style>