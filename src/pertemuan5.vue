<script setup>

import { ref,computed,watch,onMounted } from 'vue';

const activity =ref("")

const data =ref ([
    {id:1,nama:"ali",done:true},
    {id:2,nama:"ale",done:false},
    {id:3,nama:"agus",done:true}

]);

const addData = () => {
    let newData = {
        id:data.value.length+1,
        nama:activity.value,
        done:false
    }

    data.value.push(newData)
    activity.value = ""
}


const doneData = computed ( () => {
    return data.value.filter( (todo) => todo.done ==true)
})
const notDoneData = computed ( () => {
    return data.value.filter( (todo) => todo.done ==false)
})

const number = ref(0);
const refButton = ref("");

watch(number,(a,b) =>{
    if(a>=5){
        console.log("Number  Changed",a,b)
        console.log(refButton);
        
    }
})


const forMounted = ref(null);

onMounted( () =>{
    forMounted.value.textContent ="Ini bukan pertemuan 5";
})

</script>

<template>
<h1>Pertemuan 5</h1>
<h1 ref="forMounted">Ini Pertemuan 5</h1>

<p>Count :{{ number }}</p>
<button @click="number++">Klik</button>


<p>New Data :{{ activity }}</p>
<input v-model="activity">
<button @click="addData">Submit</button>


<h1>Semua Data</h1>
<ul>
    <li v-for="todo in data" :key="todo.id">{{ todo.id }}. {{ todo.nama }} - {{ todo.done }}
        <input type="checkbox" v-model="todo.done">
    </li>
</ul>
<h1>Sudah Terdata</h1>
<ul>
    <li v-for="todo in doneData" :key="todo.id">{{ todo.id }}. {{ todo.nama }} - {{ todo.done }}
        <input type="checkbox" v-model="todo.done">
    </li>
</ul>
<h1>Belum  Terdata</h1>
<ul>
    <li v-for="todo in notDoneData" :key="todo.id">{{ todo.id }}. {{ todo.nama }} - {{ todo.done }}
        <input type="checkbox" v-model="todo.done">

    </li>
</ul>

</template>

<style>
h1{
    padding: 100px;
}

p{
    color: red;
}

</style>