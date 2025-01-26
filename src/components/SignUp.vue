<script setup lang="ts">
import { ref } from 'vue'

const emit = defineEmits(['signup'])

const username = ref('')
const email = ref('')
const password = ref('')
const confirmPassword = ref('')
const error = ref('')

const handleSubmit = (e: Event) => {
  e.preventDefault()
  
  if (!username.value || !email.value || !password.value || !confirmPassword.value) {
    error.value = 'Tüm alanları doldurunuz'
    return
  }

  if (password.value !== confirmPassword.value) {
    error.value = 'Şifreler eşleşmiyor'
    return
  }

  // Gerçek uygulamada API çağrısı yapılır
  emit('signup')
}

const clearError = () => {
  error.value = ''
}
</script>

<template>
  <form @submit="handleSubmit" class="auth-form">
    <h2>Kayıt Ol</h2>
    
    <div class="form-group">
      <label>Kullanıcı Adı:</label>
      <input 
        type="text" 
        v-model.trim="username"
        @input="clearError"
        placeholder="Kullanıcı adınız"
      >
    </div>

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

    <div class="form-group">
      <label>Şifre Tekrar:</label>
      <input 
        type="password" 
        v-model="confirmPassword"
        @input="clearError"
        placeholder="********"
      >
    </div>

    <p v-if="error" class="error">{{ error }}</p>

    <button type="submit">Kayıt Ol</button>
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