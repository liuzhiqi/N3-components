<template>
 	<li class="{{prefixCls}}-timeline-item">
 		<div class="{{prefixCls}}-timeline-item-tail"></div>
 		<div :class="[prefixCls+'-timeline-item-head',icon?'fa fa-'+icon:'']" :style="style"></div>
 		<div class="{{prefixCls}}-timeline-item-content">
	 		<slot></slot>
 		</div>
 	</li>
</template>
<script>
export default{
  props: {
    icon: {
      type: String
    },
    color: {
      type: String,
      default: '#41cac0'
    },
    content: {
    },
    prefixCls: {
      type: String,
      default: 'n3'
    }
  },
  computed: {
    style () {
      return {
        'border-color': this.color,
        'color': this.color
      }
    }
  }
}
</script>