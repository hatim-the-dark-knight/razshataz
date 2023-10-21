<style>
/* Style the card component */
.card {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  background-color: rgb(41, 43, 43);
}

/* Style the image container with overlay text */
.card-image-container {
  position: relative;
}

/* Style the card image */
.card-image {
  width: 100%;
  max-width: 300px;
  height: auto;
}

/* Style the overlay text */
.overlay-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: rgba(0, 0, 0, 0.7);
  color: #fff;
  padding: 10px;
  border-radius: 5px;
}

/* Style the details on the left */
.card-details-left {
  text-align: left;
  margin: 10px;
}

/* Style the details on the right */
.card-details-right {
  text-align: right;
  margin: 10px;
}

/* Style the title */
.card-title {
  font-size: 24px;
  font-weight: bold;
}

/* Style the description */
.card-description {
  font-size: 16px;
  margin: 10px 0;
}
</style>

<template>
    <div class="card">
        <!-- Image at the top with overlay text -->
        <div class="card-image-container">
            <img :src="game.image" alt="Card Image" class="card-image" />
            <div class="overlay-text">The Game</div>
        </div>

        <!-- Left-aligned details -->
        <div class="card-details card-details-left">
            <h2 class="card-title">{{ game.name }}</h2>
            <p class="card-description">{{ game.about }}</p>
        </div>

        <button id="show-modal" @click="showModal = true">Details</button>

        <Teleport to="body">
        <!-- use the modal component, pass in the prop -->
        <modal :show="showModal" @close="showModal = false">
            <template #header>
            <h2>{{game.name}}</h2>
            </template>
            <template #body>
                <h4>{{game.about}}</h4>
                <p v-for="(rule, ind) in game.rules">
                    {{ ind+1 }}. {{ rule }}
                </p>
            </template>
        </modal>
        </Teleport>
    </div>
</template>

<script setup>
import Modal from './Modal.vue';
import { ref } from 'vue';

const showModal = ref(false)

</script>

<script>
export default {
    components: {
        Modal
    },
  props: {
    game:Object,
  },
};
</script>