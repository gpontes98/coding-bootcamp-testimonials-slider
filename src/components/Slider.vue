<template>
  <div class="container">
    <div class="testimonial">
      <img class="pattern-quotes" src="images/pattern-quotes.svg" alt="">
      <p class="testimonial-text"> {{currentTestimonial}} </p>

      <span class="testimonial-name">{{currentTestimonialName}}</span>
      <span class="testimonial-description"> {{currentTestimonialDescription}}</span>
    </div>

    <div class="slider">
      <img  class="pattern-bg" src="images/pattern-bg.svg" alt="Pattern Background">
      <img class="slider-img" alt="Dinamic Slider Image" :src="currentImage" />

      <div class="controls-slider">
        <button @click="prev" class="controls-slider-button-prev" aria-label="prev-slider">
          <img src="images/icon-prev.svg" alt="Button prev">
        </button>
        <button @click="next" class="controls-slider-button-next" aria-label="next-slider">
          <img src="images/icon-next.svg" alt="Button next">
        </button>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name:"Slider",

    data(){
      return{
        images: [
        "images/image-tanya.jpg",
          "images/image-john.jpg"
        ],
        testimonials:[
          `“ I’ve been interested in coding for a while but never taken the jump, until now. I couldn’t recommend this course enough. I’m now in the job of my dreams and so excited about the future. ”`,
          `“ If you want to lay the best foundation possible I’d recommend taking this course. The depth the instructors go into is incredible. I now feel so confident about starting up as a professional developer. ”`
        ],
        testimonialsName:[
          "Tanya Sinclair",
          "John Tarkpor"
        ],
        testimonialsDescription: [
          "UX Engineer",
          "Junior Front-end Developer"
        ],
        timer: null,
        currentIndex:0
      };  
    },

    mounted: function() {
      this.startSlide();
    },

    methods: {
      startSlide: function(){
        this.timer = setInterval(this.next, 5000);
      },
      next: function(){
        this.currentIndex += 1;
      },
      prev: function(){
        this.currentIndex -= 1;
      }
    },

    computed:{
      currentImage: function(){
        return this.images[Math.abs(this.currentIndex) % this.images.length];
      },
      currentTestimonial: function(){
        return this.testimonials[Math.abs(this.currentIndex)  % this.testimonials.length];
      },
      currentTestimonialName: function(){
        return this.testimonialsName[Math.abs(this.currentIndex)  % this.testimonialsName.length];
      },
      currentTestimonialDescription: function(){
        return this.testimonialsDescription[Math.abs(this.currentIndex)  % this.testimonialsDescription.length];
      }
    }
    
  };
</script>

<style>

</style>
