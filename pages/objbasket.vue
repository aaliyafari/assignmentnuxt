<template>
  <div>
    <Navbar/>
    <div class="m-8">
     <h6>Please choose items to your bucket</h6>
     <div class="flex flex-row ">
      <div class="basis-1/4 apple">
        <div>{{apple.name}}</div>
        <div>{{apple.count}}</div>
        <div><button v-on:click="add" >+</button><button v-on:click="remove">-</button></div>

      </div>
      <div class="basis-1/4 orange">
        <div>{{orange.name}}</div>
        <div>{{orange.count}}</div>
        <div><button v-on:click="add1">+</button><button v-on:click="remove1">-</button></div>

      </div>
      <div class="basis-1/4 grapes">
        <div >{{grapes.name}}</div>
        <div>{{grapes.count}}</div>
        <div><button v-on:click="add2" class="rounded-full">+</button><button v-on:click="remove2">-</button></div>

      </div>
     </div>
    </div>
    <div class="m-8">
      <div class="mx-32">
        <h4>Basket stack</h4>
      </div>
     <table class="w-64 mx-20 items-cener justify-center"><tr class="border-solid border-2 border-indigo-600 w-10" v-for="(basket, index) in basket.slice().reverse()" :key="index">
    <td :class="classe[basket]">{{basket}}</td>
</tr></table>
    </div>
  </div>
</template>

<script>  

import login from './login.vue';  
export default {
    
    name:login,
    
   data(){
    return{
      "apple":{
        name:"Apple",
        count:10,
        color:"#FF0000"
      },
      "orange":{
        name:"Orange",
        count:10,
        color:""
      },
      "grapes":{
        name:"Grapes",
        count:10,
        color:""
      },
      basket:[],
      classe:{
        "Apple":'apple',
        'Orange':"orange",
        "Grapes":"grapes"
    }
    }
  },
  
  methods:{
    add(){
        if(this.apple.count>0){
      this.apple.count = this.apple.count === 0 ? 0 : this.apple.count - 1;
      this.basket.push(this.apple.name)
        }
           else{
           alert("Sorry!You ran out of Apples")
           } 
        },
    remove(){
        if(this.basket.at(-1)==this.apple.name){
     this.apple.count = this.apple.count === 10 ? 10 : this.apple.count + 1;
     this.basket.pop()
        }
        else{
            alert("You have selected invalid item")
        }
    },
    add1(){
        if(this.orange.count>0){
      this.orange.count = this.orange.count === 0 ? 0 : this.orange.count - 1;
      this.basket.push(this.orange.name)
        }
        else{
            alert("There are No Enough Oranges in cart")
        }
    },
    remove1(){
        if(this.basket.at(-1)==this.orange.name){
     this.orange.count = this.orange.count === 10 ? 10 : this.orange.count + 1;
     this.basket.pop()
        }
        else{
            alert("You have selected invalid item ")
        }
    },
    add2(){
        if(this.grapes.count>0){
      this.grapes.count = this.grapes.count === 0 ? 0 : this.grapes.count - 1;
      this.basket.push(this.grapes.name)
        }
        else{
            alert("There are No Enough grapes left")
        }
    },
    remove2(){
         console.warn(this.basket.at(-1))
        if(this.basket.at(-1)==this.grapes.name){
     this.grapes.count = this.grapes.count === 10 ? 10 : this.grapes.count + 1;
     this.basket.pop()
        }
         else{
            alert("You have selected invalid item ")
         }
    },
  }

}
</script>

<style scoped>
.apple{
    background-color: red;
}
.orange{
    background-color: orange;
}
.grapes{
    background-color: blue;
}
</style>