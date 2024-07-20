<template>
    <div :style="fontstyle">
        <div class='rate' @mouseout="mouseOut">
          <span @mouseover="mouseOver(num)"  v-for='num in 5' :key="num">☆</span>
          <span class='hollow' :style="fontwidth">
            <span @mouseover="mouseOver(num)" @click="onRate(num)" v-for='num in 5' :key="num">★</span>
          </span>
        </div> 
    </div>
    </template>
    <script setup>
    import {ref,computed} from 'vue'
    
    // ...其他代码
    // 评分宽度
    let width = ref(1.5)
    function mouseOver(i){
        console.log(i)
        width.value = i 
    }
    function mouseOut(e){
        console.log(e)
        width.value = 1.5
    }

    function onRate(i){
        width.value=i
    }
    const fontwidth = computed(()=>`width:${width.value}em;`)
    
    </script>
    
    <style scoped>
    .rate{
      position:relative;
      display: inline-block;
    }
    .rate > span.hollow {
      position:absolute;
      display: inline-block;
      top:0;
      left:0;
      width:0;
      overflow:hidden;
    }
    </style>