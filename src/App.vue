<script>
export default {
  data() {
    return {
      currentSlideIndex: 0, // Index of the currently displayed slide
      slides: null, // Placeholder for the collection of slides
    }
  },
  mounted() {
    this.slides = document.querySelectorAll('.slide')
    // Display the first slide
    this.showSlide(this.currentSlideIndex)
    setInterval(this.nextSlide, 3000)
  },
  methods: {
    showSlide(index) {
      if (index < 0) {
        this.currentSlideIndex = this.slides.length - 1
      } else if (index >= this.slides.length) {
        this.currentSlideIndex = 0
      }
      this.slides.forEach((slide, i) => {
        if (i === this.currentSlideIndex) {
          slide.style.display = 'block'
        } else {
          slide.style.display = 'none'
        }
      })
    },
    prevSlide() {
      this.currentSlideIndex--;
      this.showSlide(this.currentSlideIndex);
    },
    nextSlide() {
      this.currentSlideIndex++;
      this.showSlide(this.currentSlideIndex);
    }
  }
}
</script>

<template>
  <div class="slide-container">
    <h1 class="is-size-3 has-text-weight-semibold">Image Slider</h1>
    <div class="slider mt-3">
      <img src="https://placehold.co/600x400?text=Hello+World" alt="Image1" class="slide">
      <img src="https://placehold.co/600x400?text=Hello+Jesse" alt="Image2" class="slide">
      <img src="https://placehold.co/600x400?text=Percect+Day" alt="Image3" class="slide">
      <img src="https://placehold.co/600x400?text=Green+Meadow" alt="Image4" class="slide">
      <img src="https://placehold.co/600x400?text=Small+Town" alt="Image5" class="slide">
      <img src="https://placehold.co/600x400?text=Good+Feeling" alt="Image6" class="slide">
    </div>
    <button id="prevButton" @click="prevSlide" class="button is-link mt-4 mr-2">Previous</button>
    <button id="nextButton" @click="nextSlide" class="button is-link mt-4 ml-2" >Next</button>
  </div>
</template>

<style scoped>
@import "https://cdn.jsdelivr.net/npm/bulma@1.0.0/css/bulma.min.css";

.slide-container {
  max-width: 400px;
  margin: 4rem auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f9f9f9;
  text-align: center;
}

.slider {
  position: relative;
  overflow: hidden;
  max-height: 300px;
}

.slide {
  width: 100%;
  max-height: 300px;
  transition: opacity 0.5s;
  display: none;
}



</style>
