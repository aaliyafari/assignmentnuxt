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
    props:{
        name:String,
       password:String,
       permission:String
    },
data(){
    return{
     name:'',
     password:'',
     permission:''
    }
},
methods:{
     async login(){
        let result = await axios.get(
            `http://localhost:8000/users?name=${this.name}&password=${this.password}`
            
        );
        if(result.status==200 && result.data.length>0){
            this.$router.push({name:"objbasket",props:true})
            
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