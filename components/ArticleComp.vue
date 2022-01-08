<template>
  <div>
    <div class="fd-article card is-clickable">
      <div>
        <b-image :src="data.image" ratio="2by1"></b-image>
        <p class="fd-article-title mb-2 is-size-6 has-text-weight-bold mt-3">{{ data.title }}</p>
        <div class="is-flex">
          <div class="author">
            <p class="is-size-7">{{ data.author }}</p>
          </div>
          <div>
            <p class="is-size-7 has-text-grey-light">{{ data.published_at }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "ArticleComponent",
  props: {
    data: {
      type: Object,
      default: () => [],
    },
  },
};
</script>
<style lang="scss">
.fd-article {
  border: none;
  box-shadow: none;
  .fd-article-title {
    line-height: 1rem;
  }
  .author {
    border-right: 1px solid #CCCCCC;
    padding-right: 0.5rem;
    margin-right: 0.5rem;
  }
}
</style>