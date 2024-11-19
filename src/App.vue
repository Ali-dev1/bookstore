<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Header -->
    <header class="bg-green-600 text-white p-4">
      <div class="container mx-auto flex justify-between items-center">
        <h1 class="text-2xl font-bold">BookMarket</h1>
        <nav class="flex gap-4">
          <button @click="activeTab = 'browse'" :class="['nav-link', activeTab === 'browse' ? 'font-bold' : '']">Browse</button>
          <button @click="activeTab = 'cart'" :class="['nav-link', activeTab === 'cart' ? 'font-bold' : '']">
            Cart ({{ cartItems.length }})
          </button>
          <button @click="activeTab = 'profile'" :class="['nav-link', activeTab === 'profile' ? 'font-bold' : '']">Profile</button>
        </nav>
      </div>
    </header>

    <!-- Main Content -->
    <main class="container mx-auto p-4">
      <!-- Browse Tab -->
      <div v-if="activeTab === 'browse'" class="space-y-6">
        <div class="flex justify-between items-center">
          <input 
            type="text" 
            placeholder="Search books..." 
            class="w-full max-w-md px-4 py-2 rounded-lg border border-gray-300 focus:outline-none focus:ring-2 focus:ring-green-500"
            v-model="searchQuery"
          >
        </div>

        <section>
          <h2 class="text-xl font-bold mb-4">Featured Books</h2>
          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
            <div v-for="book in featuredBooks" :key="book.id" class="card">
              <img :src="book.cover" alt="book cover" class="w-full h-48 object-cover rounded-md mb-4">
              <h3 class="font-bold text-lg">{{ book.title }}</h3>
              <p class="text-gray-600">{{ book.author }}</p>
              <p class="text-green-600 font-bold mt-2">${{ book.price }}</p>
              <button @click="addToCart(book)" class="primary-btn w-full mt-4">Add to Cart</button>
            </div>
          </div>
        </section>
      </div>

      <!-- Cart Tab -->
      <div v-if="activeTab === 'cart'" class="space-y-4">
        <h2 class="text-xl font-bold">Shopping Cart</h2>
        <div v-if="cartItems.length === 0" class="text-center py-8 text-gray-500">
          Your cart is empty
        </div>
        <div v-else class="space-y-4">
          <div v-for="item in cartItems" :key="item.id" class="card flex justify-between items-center">
            <div class="flex gap-4 items-center">
              <img :src="item.cover" alt="book cover" class="w-16 h-24 object-cover rounded">
              <div>
                <h3 class="font-bold">{{ item.title }}</h3>
                <p class="text-green-600">${{ item.price }}</p>
              </div>
            </div>
            <button @click="removeFromCart(item)" class="text-red-500 hover:text-red-700">Remove</button>
          </div>
          <div class="card">
            <p class="text-xl font-bold">Total: ${{ cartTotal }}</p>
            <button @click="checkout" class="primary-btn w-full mt-4">Checkout</button>
          </div>
        </div>
      </div>

      <!-- Profile Tab -->
      <div v-if="activeTab === 'profile'" class="max-w-md mx-auto space-y-4">
        <div class="card">
          <h2 class="text-xl font-bold mb-4">Profile</h2>
          <p class="text-lg">John Doe</p>
          <p class="text-gray-600">john.doe@email.com</p>
        </div>
        <button class="primary-btn w-full">Order History</button>
        <button class="primary-btn w-full">Settings</button>
        <button class="w-full bg-gray-500 text-white font-bold py-2 px-4 rounded-lg hover:bg-gray-600 transition-colors">
          Logout
        </button>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const activeTab = ref('browse')
const searchQuery = ref('')
const cartItems = ref([])

const featuredBooks = ref([
  {
    id: 1,
    title: 'The Great Gatsby',
    author: 'F. Scott Fitzgerald',
    price: 9.99,
    cover: 'https://images.unsplash.com/photo-1544947950-fa07a98d237f?auto=format&fit=crop&q=80&w=400'
  },
  {
    id: 2,
    title: '1984',
    author: 'George Orwell',
    price: 12.99,
    cover: 'https://images.unsplash.com/photo-1543002588-bfa74002ed7e?auto=format&fit=crop&q=80&w=400'
  },
  {
    id: 3,
    title: 'To Kill a Mockingbird',
    author: 'Harper Lee',
    price: 11.99,
    cover: 'https://images.unsplash.com/photo-1541963463532-d68292c34b19?auto=format&fit=crop&q=80&w=400'
  }
])

const cartTotal = computed(() => {
  return cartItems.value.reduce((sum, item) => sum + item.price, 0).toFixed(2)
})

const addToCart = (book) => {
  cartItems.value.push(book)
}

const removeFromCart = (book) => {
  const index = cartItems.value.findIndex(item => item.id === book.id)
  if (index > -1) {
    cartItems.value.splice(index, 1)
  }
}

const checkout = () => {
  alert('Checkout functionality coming soon!')
}
</script>

<style>
.nav-link {
  @apply hover:text-green-200 transition-colors;
}
</style>