# 元素抖动提醒
-	Vue2 封装成自定义指令
```javascript
Vue.directive('shake', {
  bind(el, binding) {
    el.addEventListener('animationend', (e) => {
      el.classList.remove('apply-shake')
    })
    if (binding.value) {
      el.classList.add('apply-shake')
    }
  },
  update(el, binding) {
    if (binding.value) {
      el.classList.add('apply-shake')
    }
  }
})
```

- 使用 

```javascript
<template>
  <div>
    <button v-shake="isShake">抖动元素</button>
    <button @click="emitShake">点击按钮</button>
  </div>
</template>

<script>

export default {
  data() {
    return {
      isShake: false
    }
  },
  methods: {
    emitShake() {
      this.isShake = false
      this.isShake = true
    }
  }
}
</script>
```
