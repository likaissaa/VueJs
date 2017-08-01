# VueJs
reliase  the lazyload method by using Vue1.js Vue 2.js

#index.html
Use JQ to show how to write the lazyload method
..............................................................
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
            Vue.directive('dom',function(value){
                var obj = value;
                if(obj!=null){
                // 如果发现没有修饰符  那么 key =el  如果有修饰符 v-dom.haha="list" 哈哈就是修饰符
                var key=Object.keys(this.modifiers)[0]||"el";
                /**
                * obj 对象
                * key 键值
                * value 实际值
                */
                Vue.set(obj,key,this.el.offsetTop)
            }
            });
            <ul class="img-ct">
              <li class="item" v-for="list in lists" >
                <a href="javascript:void(0)"><img v-dom.haha="list"   v-bind:isLoaded="list.isLoaded" v-bind:data-img="list.dataimg" v-bind:src="list.myimg">234234</a>
              </li>
            </ul>
      
      ========================vm.lists[index].haha================================
    @second method
                <yh v-ref:lists v-for="list in lists"  v-bind:lists="list" v-bind:nihao="list.isLoaded" v-bind:dataimg="list.dataimg" v-bind:myimg="list.myimg"></yh>
                Vue.component('yh',{
                  template:'\
                  <li class="item">\
                    <a href="javascript:void(0)">\
                      <img  v-bind:isload="nihao" v-bind:data-img="dataimg" v-bind:src="myimg">\
                      </a>\
                      </li>\
                  ',
                  props:['lists','nihao','dataimg','myimg'],
               })
     ============vm.$refs.lists[index].$el.offsetTop==================
     
 @index5.html  vue 1.0.7 (only one method to control the dom)
     <yh v-ref:lists v-for="list in lists"  v-bind:lists="list" v-bind:nihao="list.isLoaded" v-bind:dataimg="list.dataimg" v-bind:myimg="list.myimg"></yh>
          Vue.component('yh',{
            template:'\
            <li class="item">\
              <a href="javascript:void(0)">\
                <img  v-bind:isload="nihao" v-bind:data-img="dataimg" v-bind:src="myimg">\
                </a>\
                </li>\
            ',
            props:['lists','nihao','dataimg','myimg'],
         })
       ============vm.$refs.lists[index].$el.offsetTop==================
.................................................................
