# VueJs
reliase  the lazyload method by using Vue1.js Vue 2.js

#index.html
Use JQ to show how to write the lazyload method

#index2.html
Use Vue2 (the newest version) 
@first
  window.onload =function(){
  vm.begin()
  }
@second
 mounted
 window.addEventListener('scroll', this.begin) 
@last 
  ref  is a good method for u to control the dom elements ,
  Especially u have to combine the method v-for and ref 

 For example:
 
 html:    <div v-for="list in lists"><img ref="load"/></div>
 
 js:      vm.$refs.load[index]  to control the dom
          @vm.$refs.load[index].style.color='red'
          @vm.$refs.load[index].offsetTop;
          
          
...............................................................
#index3.html  index5.html
 description:
 when use  different and lower version in Vue you will face some problems
 @index3.html  vue 1.0.26 ( two methods to control the dom)
    @first method
    ========================vm.lists[index].haha================================
    @second method
    ============vm.$refs.lists[index].$el.offsetTop==================     
 @index5.html  vue 1.0.7 (only one method to control the dom)
     ============vm.$refs.lists[index].$el.offsetTop==================
.................................................................
