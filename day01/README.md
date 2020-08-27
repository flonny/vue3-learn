# 上手vue-3，day1(defineComponent,h,createApp)

> 刚开始用vue3.0，尽量减少工程化的架子，直接引用vue3.0 的cdn来进行基础的熟悉，在页面中引用这个链接，官方已经有vue3.0的文档，可以根据文档进行练习，[vue3.0 文档](https://v3.vuejs.org/guide/introduction.html#what-is-vue-js)
>
> ```html
> <script src="https://unpkg.com/vue@next"></script>
> ```

## vue3.0 之 Hello world
> 在vue3.0 中使用的最基础的示例事一个计数器

```html
<div id="counter">
  Counter: {{ counter }}
    <p @click="stopTimer">stop</p>
</div>
```

```javascript
const CounterApp = {
  data() {
    return {
      counter: 0,
	  timer: null
    }
  },
  methods: {
      stopTimer() {
          clearInterval(this.timer)
      }
  },
  mounted() {
    this.timer = setInterval(() => {
      this.counter++
    }, 1000)
  }
}

Vue.createApp(CounterApp).mount('#counter')
```

> 这部分代码和之前的代码其实没什么区别，只是将创建实例和将实例挂载到 dom 树这些操作更加细化，由开发人员去完成这个操作
>
> 之前的代码
>
> ```javascript
> new Vue({
>   el: '#counter',
>   data...,
> })
> ```



## 创建一个组件 (defineComponent，h)

	> defineComponent 主要用于类型推断，他会返回传给他的对象
	>
	> ```javascript
	> // implementation, close to no-op
	> export function defineComponent(options: unknown) {
	>   return isFunction(options) ? { setup: options, name: options.name } : options
	> }
	> ```
	>
	> 这个代码段上方有各种类型的推断

### 上面的demo可以修改

```javascript
const {createApp,defineComponent} = Vue
const CounterApp = defineComponent({
  data() {
    return {
      counter: 0,
	  timer: null
    }
  },
  methods: {
      stopTimer() {
          clearInterval(this.timer)
      }
  },
  mounted() {
    this.timer = setInterval(() => {
      this.counter++
    }, 1000)
  }
})
createApp(CounterApp).mount('#counter')
```

### TodoList 之 TodoItem (h)

> h 返回一个 vnode， 在render 中使用

```javascript
const {createApp,defineComponent} = Vue
const CounterApp = defineComponent({
  data() {
    return {
    }
  },

})
createApp(CounterApp).mount('#counter')
```

