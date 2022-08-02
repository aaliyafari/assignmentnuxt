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
let apple="Apple"
let orange="Orange"
let grapes="Grapes"

export default {
   data(){
    return{
      counter:10,
      orangecounter:10,
      grapecounter:10,
      basket:[]

    }
  },
  methods:{
    add(){
      this.applcounter = this.counter === 0 ? 0 : this.counter - 1;
      if(counter>0){
      this.basket.push(apple)
      }
      else{
        alert("You have No Items left")
      }
    },
    remove(){
     this.counter = this.counter === 10 ? 10 : this.counter + 1;
     this.basket.pop()
    },
    add1(){
      this.orangecounter = this.orangecounter === 0 ? 0 : this.orangecounter - 1;
      this.basket.push(orange)
    },
    remove1(){
     this.orangecounter = this.orangecounter === 10 ? 10 : this.orangecounter + 1;
     this.basket.pop()
    },
    add2(){
      this.grapecounter = this.grapecounter === 0 ? 0 : this.grapecounter - 1;
      this.basket.push(grapes)
    },
    remove2(){
     this.grapecounter = this.grapecounter === 10 ? 10 : this.grapecounter + 1;
     this.basket.pop()
    },
  }

}
</script>

<style>

</style>