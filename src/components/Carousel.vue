<template>
	<div id="carousel" class="carousel">
		<slot></slot>
		<div class="carousel-nav carousel-prev fa fa-angle-left" @click.prevent="prev"></div>
		<div class="carousel-nav carousel-next fa fa-angle-right" @click.prevent="next"></div>
    <div class="clear"></div>
	</div>
</template>

<script>
export default {
  data () {
    return {
      index: 0,
      slides: [],
      direction: null,
      dragPositions: {
        start: 0,
        end: 0
      },
      carousel: null
    }
  },
  mounted () {
    this.slides = this.$children
    this.slides.forEach((slide, i) => {
      slide.index = i
    })
    this.carousel = document.getElementById('carousel')
    this.detectDrag.bind(this)()
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
    },
    detectDrag () {
      this.carousel.addEventListener('dragstart', this.dragStart.bind(this))
      this.carousel.addEventListener('dragover', function (e) {
        e.preventDefault()
      })
      this.carousel.addEventListener('dragend', this.dragEnd.bind(this))
      console.log('detectDrag' + this)
    },
    dragStart (e) {
      this.dragPositions.start = e.x
    },
    dragEnd (e) {
      this.dragPositions.end = e.x
      if (this.dragPositions.start < this.dragPositions.end) this.prev()
      else if (this.dragPositions.start > this.dragPositions.end) this.next()
    }
  }
}

</script>

<style>
	.carousel {
		font-size: 2.8em;
		position: relative;
	  cursor: pointer;
    width: 100%;
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
  #app::before, #app::after {
    content: '';
    display: table;
    clear: both;
  }
</style>
