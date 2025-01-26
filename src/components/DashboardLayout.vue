<script setup lang="ts">
import { ref } from 'vue'
import SignIn from './SignIn.vue'
import SignUp from './SignUp.vue'
import TodoList from './TodoList.vue'

const currentView = ref('signin')
const isLoggedIn = ref(false)
const username = ref('')

const handleLogin = (user: string) => {
  username.value = user
  isLoggedIn.value = true
}

const handleLogout = () => {
  isLoggedIn.value = false
  username.value = ''
  currentView.value = 'signin'
}
</script>

<template>
  <div class="dashboard">
    <header>
      <h1>Vue.js Eğitim Dashboard</h1>
      <div v-if="isLoggedIn" class="user-info">
        <span>Hoş geldin, {{ username }}!</span>
        <button @click="handleLogout" class="logout-btn">Çıkış Yap</button>
      </div>
    </header>

    <main>
      <div v-if="!isLoggedIn" class="auth-container">
        <div class="auth-tabs">
          <button 
            :class="{ active: currentView === 'signin' }"
            @click="currentView = 'signin'"
          >
            Giriş Yap
          </button>
          <button 
            :class="{ active: currentView === 'signup' }"
            @click="currentView = 'signup'"
          >
            Kayıt Ol
          </button>
        </div>

        <SignIn 
          v-if="currentView === 'signin'"
          @login="handleLogin"
        />
        <SignUp 
          v-if="currentView === 'signup'"
          @signup="currentView = 'signin'"
        />
      </div>

      <TodoList v-else />
    </main>
  </div>
</template>

<style scoped>
.dashboard {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 30px;
}

.user-info {
  display: flex;
  align-items: center;
  gap: 10px;
}

.logout-btn {
  background-color: #dc2626;
}

.auth-container {
  max-width: 400px;
  margin: 0 auto;
}

.auth-tabs {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.auth-tabs button {
  flex: 1;
  padding: 10px;
  background-color: #374151;
}

.auth-tabs button.active {
  background-color: #3b82f6;
}
</style>