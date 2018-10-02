<template>
	<div :id="menuText">
	</div>
</template>

<script>
import Bus from '../eventBus.js'
import Utils from 'udn-newmedia-utils'
export default {
  name: 'AddmenuTitle',
  props: ['menuText', 'href', 'titleColor', 'fontColor'],
  methods: {
    handle_Emit: function() {
      const self = this
      Bus.$emit('emitHeadbarOutlinkTitle', {
        title: self.menuText
      })
    }
  },
  mounted: function(){
     this.handle_Emit()
  }
}
</script>

<style lang="scss" scoped>

</style>
