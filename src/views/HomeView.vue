import api from '../services/api'
<script setup>
import { ref, onMounted } from 'vue'
import api from '@/services/api'

const status = ref(null)

onMounted(async () => {
  try {
    const res = await api.get('/health')
    status.value = res.data.status
  } catch {
    status.value = 'error'
  }
})
</script>

<template>
  <main>
    <h1>MyApp in Vue</h1>
    <p v-if="status === 'ok'">✅ API conectada</p>
    <p v-else-if="status === 'error'">❌ No se pudo conectar</p>
    <p v-else>Conectando...</p>
  </main>
</template>