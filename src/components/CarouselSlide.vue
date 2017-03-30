<template>
<transition :name="transition">
	<div class="carousel-item" v-show="visible" :class="{visible, visible}" draggable>
		<slot></slot>
	</div>
</transition>
</template>

<script>
  export default {
    data () {
      return {
        index: 0
      }
    },
    computed: {
      transition () {
        return 'slide-' + this.$parent.direction
      },
      visible () {
        return this.index === this.$parent.index
      }
    }
  }
</script>

<style>
	@keyframes slideRightIn {
		from {
			transform: translate3d(100%, 0, 0);
		}
		to {
			transform: translate3d(0, 0, 0);
		}
	}
	@keyframes slideRightOut {
		from {
			transform: translate3d(0, 0, 0);
		}
		to {
			transform: translate3d(-100%, 0, 0);
		}
	}
	@keyframes slideLeftIn {
		from {
			transform: translate3d(-100%, 0, 0);
		}
		to {
			transform: translate3d(0, 0, 0);
		}
	}
	@keyframes slideLeftOut {
		from {
			transform: translate3d(0, 0, 0);
		}
		to {
			transform: translate3d(100%, 0, 0);
		}
	}
	.carousel-item img {
		max-width: 100%;
	}
	.carousel-item {
		position: absolute;
	}
	.visible.slide-right-enter-active {
		animation: slideRightIn .8s;
	}
	.slide-right-leave-active {
		animation: slideRightOut .8s;
	}
	.visible.slide-left-enter-active {
		animation: slideLeftIn .8s;
	}
	.slide-left-leave-active {
		animation: slideLeftOut .8s;
	}
</style>
