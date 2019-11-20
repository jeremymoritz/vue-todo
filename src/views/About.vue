<template>
  <div class="about">
    <h1>This is an about page</h1>
    <p>{{ description }}</p>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
export default {
  name: 'About',
  props: ['description']
};
</script>
