<template>
  <section>
    <page-banner :banner1="banner1"/>
    <!-- Slices block component -->
    <div class="container">
      <slice-zone type="page" :uid="$route.params.uid" />
    </div>
  </section>
</template>

<script>
// Imports for Prismic Slice components
import SliceZone from "vue-slicezone";
import PageBanner from "~/components/PageBanner.vue"

export default {
  name: "page",
  components: {
    SliceZone,
    PageBanner
  },
  head() {
    return {
      title: "Prismic Nuxt.js Multi Page Website"
    };
  },
    async asyncData({ $prismic, params, error }) {
    try{
      // Query to get post content
      const page = (await $prismic.api.getByUID('page', params.uid)).data
      // Returns data to be used in template
      return {
        banner1: page.page_banner[0],
    }
    } catch (e) {
      // Returns error page
      error({ statusCode: 404, message: 'Page not found' })
    }
  },
};
</script>
