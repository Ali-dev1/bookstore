<template>
  <ScrollView>
    <StackLayout class="p-4">
      <Label text="Shopping Cart" class="text-xl font-bold mb-4" />
      <ListView :items="items">
        <template #default="{ item }">
          <GridLayout columns="auto, *, auto" class="card">
            <Image :src="item.cover" width="60" height="90" col="0" />
            <StackLayout col="1" class="ml-2">
              <Label :text="item.title" class="font-bold" />
              <Label :text="'$' + item.price" class="text-green-600" />
            </StackLayout>
            <Button text="Remove" 
                    @tap="$emit('removeItem', item)" 
                    col="2"
                    class="bg-red-500 text-white rounded-lg px-2" />
          </GridLayout>
        </template>
      </ListView>
      <StackLayout class="mt-4 p-4 bg-gray-100 rounded-lg">
        <Label :text="'Total: $' + total" class="text-xl font-bold" />
        <Button text="Checkout" class="primary-btn mt-2" @tap="$emit('checkout')" />
      </StackLayout>
    </StackLayout>
  </ScrollView>
</template>

<script lang="ts">
import { defineComponent, computed } from 'nativescript-vue';

export default defineComponent({
  props: {
    items: {
      type: Array,
      required: true
    }
  },
  setup(props) {
    const total = computed(() => {
      return props.items.reduce((sum, item) => sum + item.price, 0).toFixed(2);
    });

    return {
      total
    };
  }
});
</script>