<script setup>
import { ref } from 'vue';


const selectedValue = ref('');

</script>

<template>
<div class="first">
         <p>SELECT YOUR</p>
        <img src="/images/ 5.jpg" alt="" class="firstimage">

         <p>CHARACTER</p>
         <select v-model="selectedValue" class="custom-select">
            <option value="1">png 6</option>
            <option value="2">png 1</option>
            <option value="3">png 2</option>
            <option value="4">png 3</option>
            <option value="5">png 4</option>
            <option value="6">png 5</option>
        </select>

        <div v-if="selectedValue === '1'">
            <div class="container">
                <img src="/images/ 6.jpg" alt="" class="custom-image">
                <h1 class="custom-heading">png 6</h1>
            </div>
        </div>

        <div v-else-if="selectedValue === '2'">
            <div class="container">
                <img src="/images/1.png" alt="" class="custom-image2">
                <h1 class="custom-heading"></h1>
            </div>
        </div>

        <div v-else-if="selectedValue === '3'">
            <div class="container">
                <img src="/images/2.png" alt="" class="custom-image3">
                <h1 class="custom-heading"></h1>
            </div>
        </div>

        <div v-else-if="selectedValue === '4'">
            <div class="container">
                <img src="/images/3.png" alt="" class="custom-image4">
                <h1 class="custom-heading"></h1>
            </div>
        </div>

        <div v-else-if="selectedValue === '5'">
            <div class="container">
                <img src="/images/4.png" alt="" class="custom-image4">
                <h1 class="custom-heading"></h1>
            </div>
        </div>

        <div v-else-if="selectedValue === '6'">
            <div class="container">
                <img src="/images/5.png" alt="" class="custom-image4">
                <h1 class="custom-heading"></h1>
            </div>
        </div>
</div>
</template>