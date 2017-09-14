## Vue 인스턴스 만들기
```instance
var vm = new Vue({
  // 옵션
})
```
Vue 함수로 Vue인스턴스를 만드는 것이 시작
## MVVM 패턴
![mvvm](https://joshua1988.github.io/images/posts/web/vuejs/view-model.png)
MVC패턴괴 비슷한 구조 <br>
ViewModel이 View로 부터 event를 받아들여 Model로 전달하고 DB나 네트워크 처리를 담당하는 Model에서 Data binding을 시켜 View로 전달
## 옵션
- el,data,methods
```vue
import Vue from 'vue'

Vue.config.productionTip = false

/* eslint-disable no-new */
var myVue = new Vue({
  el: '#app',
  data: {
    a: 1,
    message: '안녕하세요 Vue'
  },
  methods: {
    plus: function () {
      this.a++
    }
  }
})
console.log(myVue.$el)
myVue.plus()
console.log(myVue.$data.a)
```
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>firstprac</title>
</head>
<body>
    <div id="app">
        {{ message }}
    </div>
</body>
</html>
```
```output
안녕하세요 Vue
```
el옵션은 DOM 엘리먼트에 마운트 할 때 사용된다.(객체를 연결)<br>
data옵션은 Vue객체가 가지고 있는 데이터를 나타낸다.<br>
methods옵션은 Vue객체가 가지고 있는 함수를 나타낸다.<br><br>
## 옵션에 대한 접근 ($를 사용)
- myVue.$el<br>
```el
<div id="app">
        안녕하세요 Vue
    </div>
```
- myVue.$data.a<br>
```data
2
```
## 인스턴스 라이프사이클
![lifecycle](https://kr.vuejs.org/images/lifecycle.png)
```vue
new Vue({
  data: {
    a: 1,
    message: '안녕하세요 Vue'
  },
  created: function () {
    console.log('created')
  },
  mounted: function () {
    this.$nextTick(function () {
    // 모든 화면이 렌더링된 후 실행합니다.
      console.log('mounted')
    })
  }
})
```
```output
created
```
created가 실행되었지만 mounted는 실행되지 않는다.
```vue
el: '#app',
```
```output
created
mounted
```


