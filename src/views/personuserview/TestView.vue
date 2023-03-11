<template>
  <div>
    <h1>testview</h1>
    <input ref="img" type="file" name="" id="" @change="handlechange" />
    <button @click="upload">subir</button>
    //<img
      src="https://adonadog-aws.s3.sa-east-1.amazonaws.com/maxresdefault.jpg"
      alt=""
    />
  </div>
</template>

<script setup>
import { ref } from "vue";

const img = ref("");

const handlechange = () => {
  console.log(img.value.files);
};

const upload = async () => {
  const formData = new FormData();
  formData.append("file", img.value.files[0], "ayuwoki");
  const res = await fetch("http://127.0.0.1:8000/photos/upload", {
    method: "POST",
    body: formData,
  });

  console.log(formData);
};
</script>

<style></style>
