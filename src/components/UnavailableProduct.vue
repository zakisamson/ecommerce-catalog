<template>
    <div class="centering">
        <div class="container" style="position: relative; flex-direction: column; justify-content: center; align-items: center;">
            <img src="../assets/sad-face.png" alt="sad" style="position: absolute; margin: 0 auto; z-index: 1;">
            <p>This product is unavailable to show</p>
            <button @click="$emit('increase-id')" style="z-index: 2; border: 3px solid #000000; border-radius: 4px; width: 60%; padding: 10px;">Next Product</button>
        </div>
    </div>
</template>

<script>
export default {
    
}
</script>

<style>
@import '../assets/main.css';

</style>