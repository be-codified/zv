<template>
  <div>
    <c-box width="75%" margin-top="10">
      <p>Latest work</p>
      <c-heading as="h2" margin-bottom="5">
        {{ content.title }}
      </c-heading>
      <c-box margin-bottom="20" v-html="$md.render(content.description)" />
    </c-box>
    <c-box v-if="hasSwiper" width="75%" margin-top="10">
      <div class="swiper">
        <swiper ref="swiper" :options="swiperOptions">
          <swiper-slide>Slide 1</swiper-slide>
          <swiper-slide>
            <c-image
              :src="require('@/static/img/cat-1.jpg')"
              alt="Some image"
            />
          </swiper-slide>
          <swiper-slide>Slide 3</swiper-slide>
          <swiper-slide>Slide 4</swiper-slide>
          <swiper-slide>Slide 5</swiper-slide>
          <swiper-slide>Slide 6</swiper-slide>
          <swiper-slide>Slide 7</swiper-slide>
          <swiper-slide>Slide 8</swiper-slide>
          <swiper-slide>Slide 9</swiper-slide>
          <img
            slot="pagination"
            class="iphone-mockup"
            :src="require('@/assets/images/carousel/iphone-mockup.png')"
            alt=""
          />
          <div slot="pagination" class="swiper-pagination"></div>
          <div slot="button-prev" class="swiper-button-prev"></div>
          <div slot="button-next" class="swiper-button-next"></div>
        </swiper>
      </div>
    </c-box>
    <c-box
      margin-bottom="5"
      margin-left="5"
      v-html="$md.render(content.technologies)"
    />
    <p>Client {{ content.client }}</p>
  </div>
</template>

<script lang="js">
import {
  CBox,
  CHeading,
  CImage,
} from '@chakra-ui/vue';

export default {
  name: 'LatestWork',
  components: {
    CBox,
    CHeading,
    CImage,
  },
  props: {
    content: {
      type: Object,
      default: () => ({}),
    },
    hasSwiper: {
      type: Boolean,
      default: false,
    },
  },
  data () {
    return {
      swiperOptions: {
        loop: false,
        slidesPerView: 3,
        spaceBetween: 140,
        breakpoints: {
          // when window width is >= 320px
          320: {
            slidesPerView: 1,
            spaceBetween: 10
          },
          // when window width is >= 480px
          // 480: {
          //   slidesPerView: 3,
          //   spaceBetween: 30
          // },
          // when window width is >= 640px
          // 640: {
          //   slidesPerView: 4,
          //   spaceBetween: 40
          // }
        },
        pagination: {
          el: '.swiper-pagination',
          clickable: true,
        },
        navigation: {
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev',
        },
      }
    }
  },
}
</script>

<style>
.swiper {
  height: auto;
  width: 100%;
  position: relative !important;
  margin-top: 30px;
}

.swiper .swiper-container {
  padding-top: 0;
  padding-bottom: 100px;
  position: static !important;
}

.swiper .swiper-slide {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: ghostwhite;
  border-radius: 40px;
}

.swiper .swiper-slide img {
  width: 206px;
}

.swiper .swiper-pagination-bullets {
  bottom: 0;
}

.swiper .swiper-pagination-bullet-active {
  background-color: #000;
}

.swiper .swiper-button-prev,
.swiper .swiper-button-next {
  top: calc(50% - 60px);
  color: #000;
}

.swiper .swiper-button-prev {
  right: auto !important;
}

.swiper .swiper-button-next {
  left: auto !important;
}

.swiper .iphone-mockup {
  width: 320px;
  height: 484px;
  position: absolute;
  top: calc(50% - 290px);
  left: calc(50% - 160px);
  z-index: 1;
}
</style>
