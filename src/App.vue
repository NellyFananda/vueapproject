<template>
  <div id="app">
    <div class="container">
      <!-- Click Counter -->
      <div class="section">
        <h2>Click Counter</h2>
        <button @click="incrementCounter" class="btn btn-primary">Click Me</button>
        <p>Count: {{ counter }}</p>
      </div>

      <!-- Box Color Changer -->
      <div class="section">
        <h2>Box Color Changer</h2>
        <button @click="changeColor" class="btn btn-secondary">Change Color</button>
        <div :style="{ backgroundColor: boxColor }" class="color-box"></div>
      </div>

      <!-- Image Carousel -->
      <div class="section">
        <h2>Image Carousel</h2>
        <swiper-container
          :slides-per-view="1"
          :navigation="true"
          :pagination="{ clickable: true }"
          class="mySwiper"
        >
          <swiper-slide v-for="(image, index) in images" :key="index">
            <img :src="image" alt="Carousel Image" class="carousel-image" />
          </swiper-slide>
        </swiper-container>
      </div>
    </div>
  </div>
</template>

<script>
import { Navigation, Pagination, Swiper as SwiperClass } from 'swiper';
import 'swiper/swiper-bundle.css';
import { Swiper, SwiperSlide } from 'swiper/vue';

SwiperClass.use([Pagination, Navigation]);

export default {
  name: 'App',
  components: {
    Swiper,
    SwiperSlide
  },
  data() {
    return {
      counter: 0,
      boxColor: '#FFFFFF',
      images: [
        'https://cdn.pixabay.com/photo/2023/05/24/17/49/ai-generated-8015425_1280.jpg',
        'https://cdn.pixabay.com/photo/2023/11/01/17/12/ai-generated-8358416_1280.jpg',
        'https://cdn.pixabay.com/photo/2023/08/05/01/15/ai-generated-8170159_1280.jpg'
      ]
    };
  },
  methods: {
    incrementCounter() {
      this.counter += 1;
    },
    changeColor() {
      const colors = ['#C0C0C0', '#003366', '#FFD700', '#800080'];
      this.boxColor = colors[Math.floor(Math.random() * colors.length)];
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #333;
  margin-top: 60px;
}

.container {
  width: 80%;
  margin: auto;
}

.section {
  margin-bottom: 40px;
}

.btn {
  padding: 10px 20px;
  border: none;
  color: white;
  cursor: pointer;
  border-radius: 5px;
  font-size: 16px;
}

.btn-primary {
  background-color: #007bff;
}

.btn-secondary {
  background-color: #6c757d;
}

.color-box {
  width: 200px;
  height: 200px;
  margin: 20px auto;
  border: 1px solid #ddd;
}

.carousel-image {
  width: 30%;
  height: auto;
}
</style>

