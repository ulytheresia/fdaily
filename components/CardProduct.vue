<template>
  <div class="fd-card card">
    <div class="card-header">
      <div class="media-left">
        <b-image
          src="https://picsum.photos/36"
          alt="A random image"
          :rounded="true"
        ></b-image>
      </div>
      <div class="media-content">
        <p class="is-size-7 has-text-weight-bold">
          {{ capitalizeFirstLetter(card.editor) }}
        </p>
        <p class="is-size-7 has-text-grey-light">{{ card.role }}</p>
      </div>
    </div>
    <div class="card-content">
      <div class="content">
        <div class="content-header">
          <figure class="image is-64x64">
            <img :src="card.product.image" />
          </figure>
        </div>
        <div class="card-desc">
          <div>
            <p class="is-size-7">{{ card.product.rating }}</p>
          </div>
          <div>
            <AwesomeVueStarRating
              :star="Math.floor(this.card.product.rating)"
              :disabled="this.disabled"
              :maxstars="this.maxstars"
              :starsize="this.starsize"
              :hasresults="this.hasresults"
              :hasdescription="this.hasdescription"
            />
          </div>
          <div>
            <!-- API haven't provide any -->
            <p class="is-size-7">(7)</p>
          </div>
        </div>
        <p class="is-size-6 has-text-weight-bold mb-0">
          {{ card.product.name }}
        </p>
        <p class="is-size-7 has-text-weight-bold mb-1">
          {{ card.product.description }}
        </p>
        <p class="is-size-7 has-text-grey-light">Rosy Beige</p>

        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
import AwesomeVueStarRating from "awesome-vue-star-rating";
export default {
  name: "CardProduct",
  components: {
    AwesomeVueStarRating,
  },
  data() {
    return {
      ratingdescription: [
        {
          text: "Poor",
          class: "star-poor",
        },
        {
          text: "Below Average",
          class: "star-belowAverage",
        },
        {
          text: "Average",
          class: "star-average",
        },
        {
          text: "Good",
          class: "star-good",
        },
        {
          text: "Excellent",
          class: "star-excellent",
        },
      ],
      hasresults: false,
      hasdescription: false,
      starsize: "xs", //[xs,lg,1x,2x,3x,4x,5x,6x,7x,8x,9x,10x],
      maxstars: 5,
      disabled: false,
    };
  },
  props: {
    card: {
      type: Object,
      default: () => {},
    },
  },
  methods: {
    capitalizeFirstLetter(string) {
      return string.charAt(0).toUpperCase() + string.slice(1);
    },
  },
};
</script>

<style lang="scss">
.fd-card {
  height: 100%;
  border-radius: 0.5em;
  &.card {
    box-shadow: none;
    border: 0.5px solid #CCCCCC;
  }
  .card-content {
    height: 100%;
    display: flex;
    flex-flow: column;
    padding: 1rem;
    .content {
      height: 100%;

      .content-header {
        height: 150px;
        margin-bottom: 1rem;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
      }
      .card-desc {
        display: flex;
        justify-content: space-between;
        align-items: center;
      }
    }
  }
}
.star {
  color: red;
}
.star.active {
  color: red;
}
.list,
.list.disabled {
  &:hover {
    .star {
      color: red !important;
    }
    .star.active {
      color: red;
    }
  }
}
</style>