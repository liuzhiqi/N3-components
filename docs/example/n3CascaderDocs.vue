<template>
  <div class="bs-docs-section" id="级联选择"  >
    <h1 class="page-header"><a href="#级联选择" class="anchor">级联选择</a><span class="author"> </span></h1>
    <div class="bs-example">
      <n3-cascader :options="options" :on-change="selectChange" :value.sync="value" :select-change="true"></n3-cascader>
      {{value | json}}
    </div>
    <pre><code class="language-markup"><script type="language-mark-up">
    <n3-cascader :options="options" :on-change="selectChange" :value.sync="value" :select-change="true"></n3-cascader>
    </script></code></pre>
    <h2>参数</h2>
    <table class="table table-bordered">
      <thead>
        <tr>
          <th>参数名</th>
          <th>类型</th>
          <th>默认值</th>
          <th>说明</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>options</td>
          <td><code>Array</code></td>
          <td></td>
          <td><pre><code>
            [{
              value: 'zhejiang',
              label: '浙江',
              children: [{
                value: 'hangzhou',
                label: '杭州',
                children: [{
                  value: 'xihu',
                  label: '西湖',
                }],
              }],
            }, {
              value: 'jiangsu',
              label: '江苏',
              disabled:true,
              children: [{
                value: 'nanjing',
                label: '南京',
                children: [{
                  value: 'zhonghuamen',
                  label: '中华门',
                }],
              }],
            }]
          </code></pre></td>
        </tr>
        <tr>
          <td>value</td>
          <td><code>Array</code></td>
          <td></td>
          <td>需要<code>.sync</code></td>
        </tr>
        <tr>
          <td>width</td>
          <td><code>String</code></td>
          <td><code>200px</code></td>
          <td></td>
        </tr>
        <tr>
          <td>disabled</td>
          <td><code>Boolean</code></td>
          <td><code>false</code></td>
          <td></td>
        </tr>
        <tr>
          <td>placeholder</td>
          <td><code>String</code></td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <td>displayRender</td>
          <td><code>Function</code></td>
          <td><pre><code>
            function(label){
              return label.join(' / ')
            }
          </code></pre></td>
          <td></td>
        </tr>
        <tr>
          <td>select-change</td>
          <td><code>Boolean</code></td>
          <td></td>
          <td>选择值就改变</td>
        </tr>
        <tr>
          <td>on-change</td>
          <td><code>Function</code></td>
          <td></td>
          <td>值变化时候后触发</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
const options = [{
  value: 'zhejiang',
  label: '浙江',
  children: [{
    value: 'hangzhou',
    label: '杭州',
    children: [{
      value: 'xihu',
      label: '西湖',
    }],
  }],
}, {
  value: 'jiangsu',
  label: '江苏',
  disabled:true,
  children: [{
    value: 'nanjing',
    label: '南京',
    children: [{
      value: 'zhonghuamen',
      label: '中华门',
    }],
  }],
}]

const value = ['zhejiang', 'hangzhou', 'xihu']

export default {
  data () {
    return {
      options: options,
      value: value
    }
  },
  ready () {
  },
  methods: {
    selectChange (selectedValue, option) {
      console.log(this.value)
    }
  }
}
</script>

<style>

</style>
