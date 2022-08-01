<template>
  <div>
    <form>
        <h1>Login</h1>
        <div><input type="text" placeholder="username" v-model="name"/>
        </div>
        <div><input type="text" placeholder="password" v-model="password"/></div>
        <div><button v-on:click="login() " type="submit" >Submit</button><NuxtLink to="/basket"></NuxtLink></div>
        
        
    </form>
  </div>
</template>

<script>
import axios from "axios"
import { NuxtLink } from '~~/.nuxt/components'
export default {
data(){
    return{
     name:'',
     password:''
    }
},
methods:{
     async login(){
        let result = await axios.get(
            `http://localhost:3000/users?name=${this.name}&password=${this.password}`
        )
        if(result.status==200 && result.length.data>0){
            localStorage.setItem("user-info",JSON.stringify(result.data[0]))
            
        }
    }
}
}
</script>

<style>

</style>