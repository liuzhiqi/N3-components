<template>
  <div>
    <ul :class="classObj" >
      <li
          v-for="r in renderData"
          :class="liclassObj($index,r)"
          @click.prevent="handleTabListClick($index, r)"
          :disabled="r.disabled">
          <a href="#">
            {{r.header}}
            <n3-badge v-if="r.badge">{{r.badge}}</n3-badge>
          </a>
      </li>
    </ul>
    <div class="{{prefixCls}}-tab-content" v-el:tabContent>
      <slot></slot>
    </div>
  </div>
</template>

<script>
import type from 'get-type'
import n3Badge from './n3Badge'

export default {
  props: {
    pills: {
      type: Boolean
    },
    stacked: {
      type: Boolean
    },
    primary: {
      type: Boolean
    },
    justified: {
      type: Boolean
    },
    size: {
      type: String
    },
    activeIndex: {
      type: Number,
      default: 0
    },
    onChange: {
      type: Function
    },
    prefixCls: {
      type: String,
      default: 'n3'
    }
  },
  data () {
    return {
      renderData: []
    }
  },
  components: {
    n3Badge
  },
  computed: {
    classObj () {
      let {prefixCls, pills, stacked, primary, justified} = this
      let klass = {}

      klass[prefixCls + '-nav'] = true
      klass['clearfix'] = true
      klass[prefixCls + '-nav-tabs'] = true
      klass[prefixCls + '-nav-tabs-pills'] = pills
      klass[prefixCls + '-nav-tabs-stacked'] = stacked
      klass[prefixCls + '-nav-tabs-primary'] = primary
      klass[prefixCls + '-nav-tabs-justified'] = justified

      return klass
    }
  },
  methods: {
    liclassObj (index, r) {
      let {prefixCls, activeIndex} = this
      let klass = {}

      klass[prefixCls + '-nav-tabs-active'] = index === activeIndex
      klass[prefixCls + '-nav-tabs-disabled'] = r.disabled

      return klass
    },
    handleTabListClick (index, el) {
      if (!el.disabled) this.activeIndex = index
      if (type.isFunction(this.onChange)) {
        this.onChange(index, el)
      }
    }
  }
}
</script>