<style>
.card {
    background-color: rgb(46, 46, 46);
    margin-bottom: 10px;
}
</style>

<template>
    <div class="container">
        <card class="card"
        v-for="(game, index) in games"
        :key="index"
        :game="game"
        />
    </div>    
</template>

<script>
import Card from './Card.vue'
import games from '../../utils/games.json'

export default {
    components: {
        Card,
    },
    data() {
        return {
            games: games,
        };
    }
};
</script>