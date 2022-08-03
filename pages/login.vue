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
     password:'',
     permission:'',
     per:''
    }
},
methods:{
     async login(){
        let per;
        let result = await axios.get(
            `http://localhost:8000/users?name=${this.name}&password=${this.password}`
        );
        
         if(result.status==200 && result.data.length>0){
             per=result.data[0].permission
            this.$router.push({name:"objbasket",params:{per}})
            
        }
        else{
            alert("Enter the valid credential")
        }
        console.warn(per)
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