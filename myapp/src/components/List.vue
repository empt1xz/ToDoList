<script setup lang="ts">
import { ref } from "vue";
const tarefa = ref("");
const lista = ref<string[]>([]);

function AdicionarTarefa() {
  if (!tarefa.value) return;

  lista.value.push(tarefa.value);

  tarefa.value = "";
}

function remove(index: number) {
    lista.value.splice(index, 1)
}
</script>

<template>
  <main>
    <h1>Adicione suas tarefas aqui.</h1>
    <input v-model="tarefa" placeholder="Nome da tarefa" />
    <input type="button" value="Adicionar" @click="AdicionarTarefa" />
    <ul>
      <li v-for="(item, index) in lista" :key="index">

            {{ item }}
            <button @click="remove(index)">x</button>
      </li>
    </ul>
  </main>
</template>

<style scoped>
main {
  background-color: rgb(51, 29, 66);
  color: white;
  font-family: Arial, Helvetica, sans-serif;
  height: 100vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 10px;
}
</style>
