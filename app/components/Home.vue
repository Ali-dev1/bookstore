<template>
  <Page>
    <ActionBar title="BookMarket" class="header">
      <NavigationButton visibility="collapsed" />
    </ActionBar>

    <TabView androidTabsPosition="bottom" selectedIndex="0">
      <!-- Browse Tab -->
      <TabViewItem title="Browse">
        <BookList 
          :books="books" 
          :featuredBooks="featuredBooks"
          :categories="categories"
          @addToCart="addToCart" />
      </TabViewItem>

      <!-- Cart Tab -->
      <TabViewItem title="Cart">
        <Cart 
          :items="cartItems"
          @removeItem="removeFromCart"
          @checkout="checkout" />
      </TabViewItem>

      <!-- Profile Tab -->
      <TabViewItem title="Profile">
        <Profile />
      </TabViewItem>
    </TabView>
  </Page>
</template>

<script lang="ts">
import { defineComponent, ref } from 'nativescript-vue';
import BookList from './BookList.vue';
import Cart from './Cart.vue';
import Profile from './Profile.vue';

export default defineComponent({
  components: {
    BookList,
    Cart,
    Profile
  },
  setup() {
    const featuredBooks = ref([
      {
        id: 1,
        title: 'The Great Gatsby',
        author: 'F. Scott Fitzgerald',
        price: 9.99,
        cover: 'https://example.com/gatsby.jpg'
      },
      {
        id: 2,
        title: '1984',
        author: 'George Orwell',
        price: 12.99,
        cover: 'https://example.com/1984.jpg'
      }
    ]);

    const books = ref([
      {
        id: 1,
        title: 'The Great Gatsby',
        author: 'F. Scott Fitzgerald',
        price: 9.99,
        cover: 'https://example.com/gatsby.jpg'
      },
      {
        id: 2,
        title: '1984',
        author: 'George Orwell',
        price: 12.99,
        cover: 'https://example.com/1984.jpg'
      }
    ]);

    const categories = ref([
      'Fiction',
      'Non-Fiction',
      'Science',
      'History',
      'Biography',
      'Technology'
    ]);

    const cartItems = ref([]);

    const addToCart = (book) => {
      cartItems.value.push(book);
    };

    const removeFromCart = (book) => {
      const index = cartItems.value.findIndex(item => item.id === book.id);
      if (index > -1) {
        cartItems.value.splice(index, 1);
      }
    };

    const checkout = () => {
      // Implement checkout functionality
      console.log('Checkout clicked');
    };

    return {
      featuredBooks,
      books,
      categories,
      cartItems,
      addToCart,
      removeFromCart,
      checkout
    };
  }
});
</script>