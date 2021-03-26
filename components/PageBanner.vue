<template>
    <section class="highlight content-section">
        <div class="highlight-left">
            <h1 class="banner-title">
                {{ $prismic.asText(banner1.title) }}
            </h1>
            <h1 class="banner-description"> {{banner1.featured_product_1.description}} </h1>
            <h1 class="banner-price"> {{banner1.featured_product_1.price}} </h1>
            <p>
                <prismic-link class="banner-button" :field="banner1.button_link">{{ $prismic.asText(banner1.button_label)}}</prismic-link>
            </p>
        </div>
        <div class="highlight-right">
            <img :src="banner1.featured_product_1.image_url"/>
        </div>
    </section>
</template>

<script>
export default {
  props: ['banner1'],
  name: 'page-banner',
}
</script>

<style lang="sass" scoped>
.highlight
  position: relative
  overflow: auto
  background-color: grey

.highlight-left
  width: 43%
  float: left
  margin-top: 8rem
  margin-left: 10rem

.highlight-right
  width: 48%
  float: right

.banner-button
  background: black
  border-radius: 7px
  color: white
  font-size: 14px
  font-weight: 700
  padding: 15px 40px
  display: block
  width: 7rem
  &:hover
    background: #c8c9cb

.banner-title
    color: white

.banner-description
  color: white
  font-size: 30px
  font-weight: 500

.banner-price
  color: white
  font-size: 40px
  font-weight: bold

@media (max-width: 767px)
  .content-section
    margin-bottom: 2rem
  .highlight-left, .highlight-right
    width: 100%
    float: none
</style>
