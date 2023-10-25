<style>
.title {
    color: #333;
}
</style>

<template>
    <h1 class="title" @click="showCountDown = true" >CountDown</h1>
    <!-- <Teleport to="body"> -->
        <Content :show="showCountDown" @close="showCountDown = false"/>
    <!-- </Teleport> -->
</template>
  
<script setup>
import { ref } from 'vue';
import Content from './CountDown/Content.vue';

const showCountDown = ref(false);
</script>