<template>
  <StackLayout class="p-4">
    <Label text="Profile" class="text-xl font-bold mb-4" />
    <StackLayout class="card">
      <Label text="John Doe" class="text-lg font-bold" />
      <Label text="john.doe@email.com" class="text-gray-600" />
    </StackLayout>
    <Button text="Order History" class="primary-btn mt-4" />
    <Button text="Settings" class="primary-btn mt-2" />
    <Button text="Logout" class="bg-gray-500 text-white rounded-lg mt-2 p-2" />
  </StackLayout>
</template>

<script lang="ts">
import { defineComponent } from 'nativescript-vue';

export default defineComponent({
  name: 'Profile'
});
</script>