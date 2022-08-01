<template>
  <div>
    <Navbar/>
    <div class="m-8">
     <h6>Please choose items to your bucket</h6>
     <div class="flex flex-row ">
      <div class="basis-1/4 bg-red-400">
        <div>Apple</div>
        <div>{{counter}}</div>
        <div><button v-on:click="add" >+</button><button v-on:click="remove">-</button></div>

      </div>
      <div class="basis-1/4 bg-orange-500">
        <div>Orange</div>
        <div>{{orangecounter}}</div>
        <div><button v-on:click="add1">+</button><button v-on:click="remove1">-</button></div>

      </div>
      <div class="basis-1/4 bg-blue-200">
        <div >Grape</div>
        <div>{{grapecounter}}</div>
        <div><button v-on:click="add2" class="rounded-full">+</button><button v-on:click="remove2">-</button></div>

      </div>
     </div>
    </div>
    <div class="m-8">
      <div>
        <h4>Basket stack</h4>
      </div>
      <div>{{basket}}</div>
    </div>
  </div>
</template>

<script>
import { remove } from '@vue/shared';

export default {
   data(){
    return{
      counter:0,
      orangecounter:0,
      grapecounter:0,
      basket:[]

    }
  },
  methods:{
    add(){
      this.counter = this.counter === 10 ? 10 : this.counter + 1;
      this.basket.push("Apple")
    },
    remove(){
     this.counter = this.counter === 0 ? 0 : this.counter - 1;
     let basket=basket.slice(0,-1)
    },
    add1(){
      this.orangecounter = this.orangecounter === 10 ? 10 : this.orangecounter + 1;
      this.basket.push("Orange")
    },
    remove1(){
     this.orangecounter = this.orangecounter === 0 ? 0 : this.orangecounter - 1;
     basket.splice(-1)
    },
    add2(){
      this.grapecounter = this.grapecounter === 10 ? 10 : this.grapecounter + 1;
      this.basket.push("Grape")
    },
    remove2(){
     this.grapecounter = this.grapecounter === 0 ? 0 : this.grapecounter - 1;
     let basket=basket.splice(-1)
    },
  }

}
</script>

<style>

</style>