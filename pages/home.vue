<template>
  <div>
    <menu-navbar :listMenuProp="listMenu"></menu-navbar>
    <section class="section editor-choice">
      <div class="container">
        <div class="columns is-centered mb-0">
          <div class="column is-four-fifths py-2">
            <p class="is-size-6 has-text-weight-bold">Editor's Choice</p>
            <p class="is-size-7 has-text-grey-light mb-1">Curated with love</p>
          </div>
        </div>
        <div class="columns is-centered is-multiline">
          <div class="column is-four-fifths">
            <div class="columns">
              <template v-for="(card, i) in products">
                <div :key="i" class="column">
                  <card-product :card="card"></card-product>
                </div>
              </template>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="ads">
      <div class="container">
        <div class="columns is-centered">
          <div
            class="
              ads-wrapper
              column
              is-full is-multiline is-mobile
              has-background-danger-light
            "
          >
            <div class="columns">
              <div class="column is-two-fifths-desktop is-full-mobile">
                <div class="columns">
                  <div class="column">
                    <div class="ads-product">
                      <div class="left-img">
                        <b-image
                          src="https://picsum.photos/200/300"
                          webp-fallback=".jpg"
                          ratio="16by9"
                          @load="onLoad1"
                        ></b-image>
                      </div>
                    </div>
                  </div>
                  <div
                    class="
                      column
                      ads-text
                      is-flex
                      is-flex-direction-column
                      is-justify-content-center
                      is-align-content-flex-end
                    "
                  >
                    <div class="here">
                      <p class="title is-4">YOUR BEAUTY JOURNEY STARTS HERE</p>
                      <p class="has-text-justified">
                        Looking for products? Lorem ipsum dolor sit amet
                        consectetur, adipisicing elit. Rem provident illum eum?
                        Hic voluptas neque voluptatibus ut minus? Provident
                        deserunt in b.
                      </p>
                      <div class="has-text-right">
                        <b-button type="is-primary">Primary</b-button>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div class="column is-three-fifths-desktop is-full-mobile">
                <div class="columns">
                  <div class="column is-three-quarters">
                    <div class="columns">
                      <template v-for="(card, i) in productsForAds">
                        <div :key="i" class="column is-one-third">
                          <card-product :card="card"></card-product>
                        </div>
                      </template>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="hero is-primary mb-4">
      <div class="hero-body">
        <p class="title">Primary hero</p>
        <p class="subtitle">Primary subtitle</p>
      </div>
    </section>
    <section class="articles mb-5">
      <div class="container">
        <div class="columns is-centered mb-0">
          <div class="column is-four-fifths py-2">
            <p class="is-size-6 has-text-weight-bold">Lates Articles</p>
            <div class="is-flex is-justify-content-space-between">
              <p class="is-size-7 has-text-grey-light mb-1">
                So you can make better purchase decision
              </p>
              <p class="is-size-7 has-text-primary is-clickable">
                See More &#9; &#62;
              </p>
            </div>
          </div>
        </div>
        <div class="columns is-centered mb-0">
          <div class="column is-four-fifths py-2">
            <div class="columns is-multiline">
              <template v-for="(article, i) in articles">
                <div :key="i" class="column is-4">
                  <article-comp :data="article"></article-comp>
                </div>
              </template>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="reviews">
      <div class="container">
        <div class="columns is-centered mb-0">
          <div class="column is-four-fifths py-2">
            <div class="columns">
              <div class="column is-three-fifths">
                <p class="is-size-6 has-text-weight-bold">Latest Reviews</p>
                <div class="is-flex is-justify-content-space-between">
                  <p class="is-size-7 has-text-grey-light mb-1">
                    So you can make better purchase decision
                  </p>
                  <p class="is-size-7 has-text-primary is-clickable">
                    See More &#9; &#62;
                  </p>
                </div>
                <div class="columns is-multiline">
                  <template v-for="(review, i) in reviews">
                    <div :key="i" class="column is-half">
                      <review-comp :data="review"></review-comp>
                    </div>
                  </template>
                  <div
                    v-swiper="swiperOption"
                    class="w-5/6 ml-auto relative"
                    :loadtheme="false"
                  >
                    <div class="swiper-wrapper">
                      <div
                        class="swiper-slide"
                        :key="banner"
                        v-for="banner in banners"
                      >
                        <!-- Render original HTML in server, render Swiper in browser (client) -->
                        <img class="h-64 w-64" :src="banner" />
                      </div>
                    </div>
                    <div class="swiper-button-prev" slot="button-prev"></div>
                    <div class="swiper-button-next" slot="button-next"></div>
                  </div>
                </div>
              </div>
              <div class="column is-two-fifths">gambar</div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import Axios from "axios";
import MenuNavbar from "../components/MenuNavbar.vue";
import CardProduct from "../components/CardProduct.vue";
import ArticleComp from "../components/ArticleComp.vue";
import ReviewComp from "../components/ReviewComp.vue";
import { directive } from "vue-awesome-swiper";
export default {
  name: "HomePage",
  layout: "layout",
  directives: {
    swiper: directive,
  },
  components: {
    MenuNavbar,
    CardProduct,
    ArticleComp,
    ReviewComp,
  },
  data() {
    return {
      banners: ["/slider-1.png", "/slider-2.png", "/slider-3.png"],
      swiperOption: {
        slidesPerView: 3,
        spaceBetween: -10,
        slidesPerGroup: 3,
        loop: true,
        loopFillGroupWithBlank: true,
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
        },
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev",
        },
        breakpoints: {
          1024: {
            slidesPerView: 4,
            spaceBetween: 10,
          },
          768: {
            slidesPerView: 3,
            spaceBetween: 10,
          },
          640: {
            slidesPerView: 2,
            spaceBetween: 10,
          },
          320: {
            slidesPerView: 1,
            spaceBetween: 10,
          },
        },
      },
      products: [],
      articles: [],
      reviews: [],
      current: 10,
      basicRomanNumeral: ["", "I", "II", "III"],
      listMenu: [
        {
          title: "SKINCARE",
          display: true,
        },
        {
          title: "MAKE UP",
          display: true,
        },
        {
          title: "BODY",
          display: true,
        },
        {
          title: "HAIR",
          display: true,
        },
        {
          title: "FRAGRANCE",
          display: true,
        },
        {
          title: "NAILS",
          display: true,
        },
        {
          title: "TOOLS",
          display: true,
        },
        {
          title: "BRANDS",
          display: true,
        },
      ],
    };
  },
  created() {
    this.getProducts();
  },
  methods: {
    getProducts() {
      const url = "https://virtserver.swaggerhub.com/hqms/FDN-WP/0.1/wp";
      Axios.get(url).then((resp) => {
        console.log("resp", resp.data);
        this.products = resp.data[`editor's choice`];
        this.productsForAds = this.products.slice(2);
        this.articles = resp.data[`latest articles`];
        this.reviews = resp.data[`latest review`];
      });
    },
  },
};
</script>

<style lang="scss">
.ads {
  margin-bottom: 1rem;
  .ads-wrapper,
  .ads-text {
    height: 375px;
  }
  .ads-product {
    position: relative;
    .left-img {
      position: absolute;
      top: 220px;
      width: 250px;
      left: -12px;
    }
  }
}
</style>