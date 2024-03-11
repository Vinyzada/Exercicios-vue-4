<script setup>
import { ref, computed, reactive } from 'vue'

const cidades = ref([
  'São Paulo',
  'Rio de Janeiro',
  'Belo Horizonte',
  'Salvador',
  'Fortaleza',
  'Curitiba',
  'Manaus',
  'Recife',
  'Porto Alegre',
  'Brasília'
])

const novoItem = ref('')

function remover(key) {
  cidades.value.splice(key, 1)
}

function adicionar() {
  cidades.value.push(novoItem.value)
  novoItem.value = ''
}

const organizar = computed(() => {
  return cidades.value.sort()
});

</script>

<template>
  <ul>
    <li v-for="(cidade, key) in organizar" :key="key">
      {{ cidade }} -- <button @click="remover(key)">remover</button>
    </li>
  </ul>
  <input type="text" v-model="novoItem" />
  <button @click="adicionar()">adicionar</button>
</template>

<style scoped></style>
