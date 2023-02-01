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
      <button @click="post_like" class="col-3 btn">
        <i v-if="data.span" class="bx bxs-heart"></i>
        <i v-if="!data.span" class="bx bx-heart"></i>{{ likes }}
      </button>
      <img class="col-6 border" src="../assets/log.jpeg" />
      <button class="col-3 btn">
        <i class="bx bxs-star"></i>
      </button>
    </div>
  </div>
</template>

<script setup>
import { onMounted, reactive } from "@vue/runtime-core";

const props = defineProps({
  storeid: Number,
  id: Number,
  name: String,
  category: String,
  price: Number,
  open: Boolean,
  likes: Number,
});

const emit = defineEmits(["funt", "funt2"]);

const data = reactive({
  span: "",
});

const post_like = async () => {
  const payload = {
    id: props.id,
  };

  const res = await fetch(`http://127.0.0.1:8000/post_like`, {
    method: "POST",
    body: JSON.stringify(payload),
    headers: {
      "Content-type": "application/json; charset=UTF-8",
      Authorization: `Bearer ${localStorage.getItem("token")}`,
    },
  });

  emit("funt");
};

const likess = async () => {
  const payload = {
    id: props.id,
  };

  const res = await fetch(`http://127.0.0.1:8000/user_like`, {
    method: "POST",
    body: JSON.stringify(payload),
    headers: {
      "Content-type": "application/json; charset=UTF-8",
      Authorization: `Bearer ${localStorage.getItem("token")}`,
    },
  });

  const da = await res.json();
  data.span = da;
  console.log(da);
};

onMounted(() => {
  likess();
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
