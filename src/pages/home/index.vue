<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
</script>

<template>
<div class="big_box">
    <div class="trenable_box">
      <div class="piece piece1"></div>
      <div class="piece piece2"></div>
      <div class="piece piece3"></div>
      <div class="piece piece4"></div>
      <div class="piece piece5"></div>
      <div class="piece piece6"></div>
      <div class="piece piece7"></div>
      <div class="piece piece8"></div>
    </div>
</div>

  
</template>

<style scoped lang="scss">
    @for $i from 1 to 8 {
      .piece#{$i} {
        transform: rotate(-45deg * $i);
      }
    }
.big_box {
  .trenable_box {
    position: relative;
    width: 150px;
    height: 300px;
    border-radius: 0 150px 150px 0;
    transform-origin: left center;
    background-image: linear-gradient(135deg, #f6d365, #f6d365 105px, transparent 105px);
    .piece {
        position: absolute;
        left: 0;
        top: 0;
        width: 150px;
        height: 300px;
        transform-origin: left center;
        border-radius: 0 150px 150px 0;
         &:nth-child(2n) {
            background-image: linear-gradient(135deg, #f6d365, #f6d365 105px, transparent 105px);
        }
        &:nth-child(2n+1) {
            background-image: linear-gradient(135deg, #ff5858, #ff5858 105px, transparent 105px);
        }

    }

  }
}

</style>
