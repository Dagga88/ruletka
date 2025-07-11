<script setup>
import { useRoute, useRouter } from 'vue-router'
import { onMounted } from 'vue'
import { useUserStore } from '@/stores/UserStore.js'

const route = useRoute()
const router = useRouter()
const userStore = useUserStore()

onMounted(async () => {
  try {
    const access = route.query.access
    const refresh = route.query.refresh

    if (access && refresh) {
      // Сохраняем в localStorage с правильными ключами
      localStorage.setItem('access_token', access)
      localStorage.setItem('refresh_token', refresh)

      // Обновляем состояние store
      userStore.setTokens(access, refresh)
      userStore.setAuth(true)
      await userStore.setUser()

      // Очищаем URL от query-параметров
      router.replace({ path: '/', query: {} })
    } else {
      console.error('Access or refresh token missing in callback URL')
      router.replace('/')
    }
  } catch (error) {
    console.error('Error during Steam callback:', error)
    router.replace('/')
  }
})
</script>