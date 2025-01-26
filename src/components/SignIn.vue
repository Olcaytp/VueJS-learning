<script setup lang="ts">
import { ref } from 'vue'

const emit = defineEmits(['login'])

const email = ref('')
const password = ref('')
const error = ref('')

const handleSubmit = (e: Event) => {
  e.preventDefault()
  
  if (!email.value || !password.value) {
    error.value = 'Tüm alanları doldurunuz'
    return
  }

  // Gerçek uygulamada API çağrısı yapılır
  emit('login', email.value.split('@')[0])
}

const clearError = () => {
  error.value = ''
}
</script>

<template>
  <form @submit="handleSubmit" class="auth-form">
    <h2>Giriş Yap</h2>
    
    <div class="form-group">
      <label>Email:</label>
      <input 
        type="email" 
        v-model.trim="email"
        @input="clearError"
        placeholder="ornek@email.com"
      >
    </div>

    <div class="form-group">
      <label>Şifre:</label>
      <input 
        type="password" 
        v-model="password"
        @input="clearError"
        placeholder="********"
      >
    </div>

    <p v-if="error" class="error">{{ error }}</p>

    <button type="submit">Giriş Yap</button>
  </form>
</template>

<style scoped>
.auth-form {
  background: #1f2937;
  padding: 20px;
  border-radius: 8px;
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input {
  width: 100%;
  padding: 8px;
  border: 1px solid #374151;
  border-radius: 4px;
  background: #374151;
  color: white;
}

.error {
  color: #ef4444;
  margin: 10px 0;
}
</style>