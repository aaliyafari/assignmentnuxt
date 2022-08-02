<template>
  <div>
    <div class="border border-indigo-600 m-8">
        <div class="justify-items-center"><h1>Login</h1></div>
        <div><input type="text" placeholder="username" v-model="name"/>
        </div><br/>
        <div><input type="password"  placeholder="password" v-model="password"/></div><br/>
        <div><button @click="login">Submit</button></div>
  </div>
  </div>
</template>

<script>
import axios from "axios"
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
            `http://localhost:8000/users?name=${this.name}&password=${this.password}`
            
        );
        // console.warn(result)
        if(result.status==200 && result.data.length>0){
            this.$router.push({name:"basket"})
            
        }
        else{
            alert("Enter the valid credential")
        }
    }
}
}
</script>

<style>
input{
    border: solid black 2px;
}
button{
    border: solid black 1px;
}
</style>