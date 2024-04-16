<template>
  <q-page class="flex flex-center">
    <img
      alt="Imagem feliz"
      :src="urlsComputed"
      style="width: 200px; height: 200px"
    />
    <q-btn color="primary" :onclick="() => getImageUrl()" label="Primary" />
  </q-page>
</template>

<script setup>
import { ref, computed } from "vue";

defineOptions({
  name: "IndexPage",
});

const imagesDatabase = [
  "https://i.pinimg.com/564x/aa/d6/9f/aad69faff0761571b238fbd0ae4baa57.jpg",
  "https://www.momentodivino.com.br/img/webp/imagens10/bom-dia-60559x8jFVj3gp.webp",
];

const imagesUrl = ref("Urls");
imagesUrl.value = imagesDatabase[getRandomInt(imagesDatabase.length)];

const urlsComputed = computed({
  // getter
  get() {
    return imagesUrl.value;
  },
  // setter
  set() {
    imagesUrl.value = getImageUrl();
  },
});

const getImageUrl = () => {
  const randomInt = getRandomInt(imagesDatabase.length);
  imagesUrl.value = imagesDatabase[randomInt];
};

function getRandomInt(max) {
  return Math.floor(Math.random() * max);
}
</script>
