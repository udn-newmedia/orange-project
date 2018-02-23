<template>
	<div class="bannerModel" :style="{backgroundColor: backgroundColor}">
		<img :src="src" :alt="alt" :title='title' :style="{backgroundColor: backgroundColor}">
	</div>
</template>

<script>
export default {

  name: 'banner',
  props: ['src', 'alt', 'title', 'backgroundColor'],
  data () {
    return {

    }
  }
}
</script>

<style lang="scss" scoped>
.bannerModel{
	width: 100%;
	position: relative;
	top: 0;
	left: 0;
	padding: 0;
	img{
		width: 100%;
		max-height: 100%;
	}
}
@media screen and (min-width: 1024px) {
	.bannerModel{
		padding: 0 10%;
	}
}
</style>