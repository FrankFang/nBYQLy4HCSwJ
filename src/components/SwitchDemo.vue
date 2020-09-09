<template>
<div class="demo-wrapper">
  <div class="demo">
    <component :is="SwitchDemo1" />
  </div>
  <div class="demo-actions">
    <Button>查看代码</Button>
  </div>
  <div class="demo-code">
    <pre class="language-html" v-html="x"></pre>
  </div>
</div>
</template>

<script lang="ts">
import SwitchDemo1 from './Switch1.demo.vue'
import Button from '../lib/Button.vue'
import 'prismjs';
import 'prismjs/themes/prism.css';
import { ref } from 'vue';
export default {
  components: {
    Button
  },
  setup() {
    const Prism: any = (window as any).Prism
    const x = Prism.highlight(SwitchDemo1.__demo, Prism.languages.html, 'html')
    return {
      x,
      SwitchDemo1
    }
  }
}
</script>

<style lang="scss" scoped>
$border-color: #d9d9d9;

.demo {
  padding: 16px;

  &-wrapper {
    border: 1px solid $border-color;
  }

  &-actions {
    padding: 4px;
    border-top: 1px dashed $border-color;
  }

  &-code {
    padding: 4px;
    border-top: 1px dashed $border-color;
    > pre{
      line-height: 1.1;
      font-family: Consolas, 'Courier New', Courier, monospace;
      margin: 0;
    }
  }
}
</style>
