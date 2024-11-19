<template>
  <ScrollView>
    <StackLayout class="p-4">
      <SearchBar hint="Search books..." @textChange="onSearch" class="mb-4" />
      
      <!-- Featured Books -->
      <Label text="Featured Books" class="text-xl font-bold mb-2" />
      <ListView :items="featuredBooks" height="200">
        <template #default="{ item }">
          <GridLayout columns="auto, *" class="card">
            <Image :src="item.cover" width="80" height="120" col="0" />
            <StackLayout col="1" class="ml-2">
              <Label :text="item.title" class="font-bold" />
              <Label :text="item.author" class="text-gray-600" />
              <Label :text="'$' + item.price" class="text-green-600 font-bold" />
              <Button text="Add to Cart" class="primary-btn" @tap="$emit('addToCart', item)" />
            </StackLayout>
          </GridLayout>
        </template>
      </ListView>
    </StackLayout>
  </ScrollView>
</template>

<script lang="ts">
import { defineComponent, ref } from 'nativescript-vue';

export default defineComponent({
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

    const onSearch = (event) => {
      // Implement search functionality
    };

    return {
      featuredBooks,
      onSearch
    };
  }
});
</script>