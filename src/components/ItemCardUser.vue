<template>
    
    <div class="montans card mt-3">
      <p class="title p-1 m-1">{{ name }}</p>
      <div class="x border">
        <router-link
            :to="`/guielditem/${storeid}/${id}/${name}/${price}/${open}`"
            style="text-decoration: none; color: inherit"
          >
        <div class="s container">
            <div><span class="spa">category: </span> {{ category }}</div>
            <div><span class="spa">price:</span> {{ price }}</div>

            <button
              class="openbutton"
              :style="
                open == true
                  ? 'background-color: #4efc03;color:green'
                  : 'background-color: #fc3f3f;color:#8f2121'
              "
            >
              open: {{ open }}
            </button>
        </div>
        </router-link>
      </div>
      <div class="row">
        <div class="container"></div>
        <button class="col-3 btn"><i class="bx bxs-like"></i>15</button>
        <img class="col-6 border" src="../assets/log.jpeg" />
        <button class="col-3 btn"><i class="bx bxs-star"></i></button>
      </div>
    </div>
  </template>
  
  <script setup>
  const props = defineProps({
    storeid:Number,
    id:Number,
    name: String,
    category: String,
    price: Number,
    open: Boolean
  });
  </script>
  
  <style>
  .montans {
    font-family: sans-serif;
  
    box-shadow: rgba(49, 255, 221, 0.25) 0px 6px 12px -2px,
      rgba(28, 205, 190, 0.508) 0px 3px 7px -3px;
    border-radius: 20px;
    width: 200px;
    color: black;
    box-shadow: rgba(50, 50, 93, 0.25) 0px 6px 12px -2px,
    rgba(0, 0, 0, 0.3) 0px 3px 7px -3px;
  }
  
  .montans:hover {
    background-color: rgb(230, 230, 230);
  }
  
  .title {
    text-align: center;
    font-size: 20px;
    font-weight: bold;
  }
  .x {
    font-size: 12px;
    font-weight: bold;
  }
  </style>