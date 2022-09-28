<template>
    <div class="relative rounded-lg mb-8 p-4 pb-0 bg-dark-grayish-blue w-80 h-[19rem] text-light-cyan ">
        <p class="text-xs pt-6 text-neon-green font-normal uppercase tracking-widest">Advice #{{ adviceNo }}</p>

        <p class="mt-4 text-xl pt-2 p-3 mb-3">
           "{{ advice }}"
        </p>

        <svg  width="295" height="16" xmlns="http://www.w3.org/2000/svg"><g fill="none" fill-rule="evenodd"><path fill="#4F5D74" d="M0 8h122v1H0zM173 8h122v1H173z"/><g transform="translate(138)" fill="#CEE3E9"><rect width="6" height="16" rx="3"/><rect x="14" width="6" height="16" rx="3"/></g></g></svg>

        <button @click="fetchAdvice" class="bg-neon-green  p-4 rounded-full absolute bottom-[-1.5rem] left-[8.4rem]">
            <svg width="24" height="24" xmlns="http://www.w3.org/2000/svg"><path d="M20 0H4a4.005 4.005 0 0 0-4 4v16a4.005 4.005 0 0 0 4 4h16a4.005 4.005 0 0 0 4-4V4a4.005 4.005 0 0 0-4-4ZM7.5 18a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm0-9a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm4.5 4.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm4.5 4.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm0-9a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Z" fill="#202733"/></svg>
        </button>
       
    </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue';

const adviceNo = ref(null)
const advice = ref(null)

 function fetchAdvice(){
    fetch('https://api.adviceslip.com/advice')
        .then(res => res.json())
        .then(data => data.slip)
        .then(output => {
            adviceNo.value = output.id
            advice.value = output.advice
        })
}


onMounted(() => fetchAdvice())

</script>

<style scoped>
button:hover{
    box-shadow: 1px -3px 20px 4px hsl(150, 100%, 66%)
}
</style>
