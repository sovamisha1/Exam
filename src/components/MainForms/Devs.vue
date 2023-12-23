<template>
  <div class="slider">
    <div class="slide-wrapper">
      <transition name="slide">
        <img
          :key="currentImage"
          :src="images[currentImage]"
          :alt="captions[currentImage]"
        />
      </transition>
      <p>{{ captions[currentImage] }}</p>
    </div>
    <button @click="nextImage">Next</button>
  </div>
</template>

<script>
export default {
  name: "DevsRevew",
  data() {
    return {
      images: [
        "https://i.47news.ru//titles/2023/07/20230710_ltpzmowtk6bv7cci0811.jpg",
        "https://avatars.mds.yandex.net/get-games/1892995/2a00000187858ad39acc1a5f6d58565d31e7/orig",
        "https://avatars.dzeninfra.ru/get-zen_doc/9632065/pub_6431d8bd027647591411544d_6431d943ee20a3484b303467/scale_1200",
      ],
      captions: [
        "+7 (911) 995-78-22",
        "+7 (901) 895-38-24",
        "+7 (962) 975-21-75",
      ], // Подписи к изображениям
      currentImage: 0,
    };
  },
  methods: {
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.images.length;
    },
  },
};
</script>

<style>
.slider {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  text-align: center;
}

.slide-wrapper {
  position: relative;
  max-width: 100%;
  overflow: hidden;
  height: 400px; /* Высота вашего слайдера */
  margin-bottom: 20px;
}

img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

p {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  color: white;
  padding: 10px;
  margin: 0;
}

button {
  margin-top: 20px;
}

.slide-enter-active {
  transition: transform 0.5s;
}
.slide-leave-active {
  transition: transform 0.5s;
}
.slide-enter,
.slide-leave-to {
  transform: translateX(-100%);
}
.slide-enter-to,
.slide-leave {
  transform: translateX(100%);
}
</style>
