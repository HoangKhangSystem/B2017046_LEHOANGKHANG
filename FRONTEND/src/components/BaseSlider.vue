<template>
   <div class="slider-box">
      <div class="slider-content">
         <Splide :options="options" aria-label="My Favorite Images">
            <SplideSlide>
               <img src="../images/slider01.webp" alt="Sample 1" />
            </SplideSlide>
            <SplideSlide>
               <img src="../images/slider02.webp" alt="Sample 2" />
            </SplideSlide>
            <SplideSlide>
               <img src="../images/slider03.webp" alt="Sample 2" />
            </SplideSlide>
            <SplideSlide>
               <img src="../images/slider04.webp" alt="Sample 2" />
            </SplideSlide>
         </Splide>
      </div>
   </div>
</template>

<script>
import { Splide, SplideSlide } from "@splidejs/vue-splide";
import { defineComponent } from "vue";

export default defineComponent({
   components: {
      Splide,
      SplideSlide,
   },

   setup() {
      const options = {
         rewind: true,
         gap: "1rem",
         autoplay: true,
      };

      return { options };
   },
});
</script>

<style scoped>
.splide__slide img {
   width: 100%;
   height: 450px;
   object-fit: cover; /* Bao phủ toàn bộ khung hình */
   display: block;
   border-radius: 10px;
   /* margin-bottom: 10%; */
}
.content {
   /* margin-top: 5px; */
   /* position: absolute; Để đưa nội dung vào trong khung ảnh */
   right: 10px;
   bottom: 20px;
   width: 400px;
   text-align: justify;
   background-color: #333;
   padding: 7px 7px 12px;
   border-radius: 3px;
   opacity: 0.85;
}
.content a {
   text-decoration: none;
   color: white;
   display: inline-block;
   line-height: 24px;
   text-transform: uppercase;
}
.slider-box {
   margin-bottom: 5%;
   width: auto;
   height: inherit;
}
</style>
