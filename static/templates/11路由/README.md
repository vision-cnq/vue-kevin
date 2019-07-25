
 # 路由
 
     Vue.js + vue-router 可以很简单的实现单页应用。
     <router-link>是一个组件，该组件用于设置一个导航链接，切换不同HTML内容。
     to属性为目标地址，即要显示的内容。
     点击过的导航链接都会加上样式 class ="router-link-exact-active router-link-active"。
  
 ## <router-link>的相关属性
 
 ### to
   >表示目标路由的链接。 当被点击后，内部会立刻把 to 的值传到 router.push()，所以这个值可以是一个字符串或者是描述目标位置的对象。
    
    <!-- 字符串 -->
    <router-link to="home">Home</router-link>
    
    <!-- 渲染结果 -->
    <a href="home">Home</a>
    
    <!-- 使用 v-bind 的 JS 表达式 -->
    <router-link v-bind:to="'home'">Home</router-link>
    
    <!-- 不写 v-bind 也可以，就像绑定别的属性一样 -->
    <router-link :to="'home'">Home</router-link>
    
    <!-- 同上 -->
    <router-link :to="{ path: 'home' }">Home</router-link>
    
    <!-- 命名的路由 -->
    <router-link :to="{ name: 'user', params: { userId: 123 }}">User</router-link>
    
    <!-- 带查询参数，下面的结果为 /register?plan=private -->
    <router-link :to="{ path: 'register', query: { plan: 'private' }}">Register</router-link>

 ### replace
  >设置 replace 属性的话，当点击时，会调用 router.replace() 而不是 router.push()，导航后不会留下 history 记录。
   
    <router-link :to="{ path: '/abc'}" replace></router-link>

 ### append
  >设置 append 属性后，则在当前 (相对) 路径前添加基路径。例如，我们从 /a 导航到一个相对路径 b，如果没有配置 append，则路径为 /b，如果配了，则为 /a/b
  
    <router-link :to="{ path: 'relative/path'}" append></router-link>
  
 ### tag
  >有时候想要 <router-link> 渲染成某种标签，例如\<li>。于是我们使用 tag prop 类指定何种标签，同样它还是会监听点击，触发导航。
  
    <router-link to="/foo" tag="li">foo</router-link>
    <!-- 渲染结果 -->
    <li>foo</li>
 
 ### active-class
  >设置 链接激活时使用的 CSS 类名。可以通过以下代码来替代。
  
    <style>
       ._active{
          background-color : red;
       }
    </style>
    <p>
       <router-link v-bind:to = "{ path: '/route1'}" active-class = "_active">Router Link 1</router-link>
       <router-link v-bind:to = "{ path: '/route2'}" tag = "span">Router Link 2</router-link>
    </p>
    注意这里 class 使用 active_class="_active"。
  
 ### exact-active-class
  >配置当链接被精确匹配的时候应该激活的 class。可以通过以下代码来替代。
  
    <p>
       <router-link v-bind:to = "{ path: '/route1'}" exact-active-class = "_active">Router Link 1</router-link>
       <router-link v-bind:to = "{ path: '/route2'}" tag = "span">Router Link 2</router-link>
    </p>
    
 ### event
  >声明可以用来触发导航的事件。可以是一个字符串或是一个包含字符串的数组。
  
    <router-link v-bind:to = "{ path: '/route1'}" event = "mouseover">Router Link 1</router-link>
    以上代码设置了 event 为 mouseover ，及在鼠标移动到 Router Link 1 上时导航的 HTML 内容会发生改变。
