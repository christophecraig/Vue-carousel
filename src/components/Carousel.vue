<template>
	<div class="carousel">
		<slot></slot>
		<div class="carousel-nav carousel-prev fa fa-angle-left" @click.prevent="prev"></div>
		<div class="carousel-nav carousel-next fa fa-angle-right" @click.prevent="next"></div>
	</div>
</template>

<script>
export default {
  data () {
    return {
      index: 0,
      slides: [],
      direction: null
    }
  },
  mounted () {
    this.slides = this.$children
    this.slides.forEach((slide, i) => {
      slide.index = i
    })
  },
  methods: {
    next () {
      this.index++
      this.direction = 'right'
      if (this.index >= this.$children.length) {
        this.index = 0
      }
    },
    prev () {
      this.index--
      this.direction = 'left'
      if (this.index < 0) {
        this.index = this.$children.length - 1
      }
    }
  }
}
</script>

<style>
	.carousel {
		font-size: 2.8em;
		position: relative;
	}
	.carousel-nav {
		display: block;
		border-radius: 0;
		cursor: pointer;
		background-color: rgba(255,255,255,0.55);
		position: absolute;
		top: 80%;
		height: 64px;
		line-height: 64px;
		width: 64px;
	}
	.carousel-prev {
		left: 42%;
	}
	.carousel-next {
		right: 42%;
	}
</style>
