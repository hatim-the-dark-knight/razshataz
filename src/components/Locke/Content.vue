<style>
.content {
    color: aliceblue;
    /* background-image: url("/src/assets/locke-bg.jpg"); */
}

.header {
    width: 100%;
    grid-area: header;
}
.left-col {
    width: 200px;
    grid-area: left-col;
}
.mid-col {
    width: 300px;
    grid-area: mid-col;
}
.right-col {
    width: 100px;
    grid-area: right-col;
}

.content {
    display: grid;
    grid-template-areas: 
    'header header header header header'
    'left-col left-col mid-col mid-col right-col';
    gap: 1px;
    padding: 1px;
    background-color: aliceblue;
}

.content > div {
    background-color: rgb(45, 45, 45);
    /* padding: 20px 0; */
}

.header h2 {
    text-align: end;
    padding-right: 2rem;
    padding-top: 1rem;
}

.left-col {
    display: flex;
    padding-top: 30px;
    align-items: start;
    justify-content: center;
}

.screen {
    background: snow;
    color: black;
    width: 75%;
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: x-large;
}

.left-bottom {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    margin-top: 10px;
}

.mid-col {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.digits {
    margin-top: 20%;
    display: flex;
    flex-wrap: wrap; /* Wrap digits to the next row when needed */
    justify-content: center;
    padding: 0px 20px 30px 20px;
}

.retro-btn {
    background: snow;
    border-radius: 5px;
    width: 64px;
    height: 64px;
    margin: 5px; /* Add some margin between buttons for spacing */
    display: flex;
    align-items: center;
    justify-content: center;
    color: rgb(38, 38, 38); /* Text color for the button */
    font-weight: 600;
    font-size: large;
    flex-grow: 0;
}

.right-col {
    display: flex;
    align-items: center;
    justify-content: left;
}

.submit-btn {
    width: 75px;
    height: 75px;
    border-radius: 50%;
    background-color: rgb(244, 36, 36);
}

</style>

<template>
    <div class="content">
        <div class="header">
            <h2>verite</h2>
        </div>
        <div class="left-col">
            <div class="screen" id="screen">{{screenValue}}</div>
            <div class="left-bottom">
                <div class="inp-0">{{ inp[0] }}</div>
                <div class="inp-1">{{ inp[1] }}</div>
                <div class="inp-2">{{ inp[2] }}</div>
                <div class="inp-3">{{ inp[3] }}</div>
            </div>
        </div>
        <div class="mid-col">
            <div class="digits">
                <span v-for="n in digits" class="retro-btn" @click="handleAppend">
                    {{ n }}
                </span>
                <span class="retro-btn" @click="handleDelete">
                    C
                </span>
            </div>
        </div>
        <div class="right-col">
            <div class="submit-btn" @click="handleSubmit"></div>
        </div>
    </div>
</template>

<script setup>
import { ref } from "vue";

const digits = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0];

let screenValue = ref("0 0 0 0");

let code = [3, 4, 5, 6];
let inp = [];

function appendToScreen(val) {
    if(parseInt(screenValue.value.split(" ").join(""), 10).toString().length < 4) {
        screenValue.value = screenValue.value.slice(2) + ` ${val}`;
        inp = screenValue.value.split(" ").map(Number);
    }
}

function deleteFromScreen() {
    screenValue.value = "0 " + screenValue.value.slice(0, -2);
    inp = screenValue.value.split(" ").map(Number);
}

function validateInput() {
    
} 

function handleAppend(e) {
    appendToScreen(e.target.innerHTML);
}

function handleDelete(e) {
    deleteFromScreen(e.target.innerHTML);
}

function handleSubmit() {
    console.log(inp);
    validateInput();
}


</script>