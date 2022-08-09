<template>
<center>
    <div class="border border-black-600 mt-48 center w-80 bg-slate-200">
        <div class="center m-2"><h1>Login</h1></div>
        <div class="mx-4"><input type="text" class="bg-slate-200 pl-2"  placeholder="username" v-model="name"/>
        </div><br/>
        <div class="mx-4"><input type="password" class="bg-slate-200 pl-2"  placeholder="password" v-model="password"/></div><br/>
        <div><button class="center bg-slate-400" @click="login">Submit</button></div>
  </div>
</center>
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
            this.$router.push({name:"basket",params:{per}})
            
        }
        else{
            alert("Enter the valid credentials")
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