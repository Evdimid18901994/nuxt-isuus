<template>
    <header class = "flex flex-row w-full bg-green-400 border-b-2 border-gray-400">
        <div class = "basis-1/4 items-center justify-start px-8">
            <img src="assets/images/arizonalogo.png" class = "w-16 h-16 bg-transparent">
        </div>
        <div class = "basis-1/4">
        </div>
        <nav class = "basis-1/2 flex flex-row items-center justify-end px-8 gap-4">
            <NuxtLink to = "/" class = "my-auto p-2 hover:bg-gray-500 hover:text-white">Home</NuxtLink>
            <NuxtLink to = "/Lab3" class = "my-auto p-2 hover:bg-gray-500 hover:text-white">Lab3</NuxtLink>
            <NuxtLink to = "/login" class = "my-auto p-2 hover:bg-gray-500 hover:text-white">LogIn</NuxtLink>
            <NuxtLink to = "/logout" class = "my-auto p-2 hover:bg-gray-500 hover:text-white">LogOut</NuxtLink>
        </nav>
    </header>

    <main :class = "['p-5', 'flex', mes >5 ?'bg-green-100': 'bg-blue-200', 'h-screen', 'items-baseline', 'flex-col']">
        <h1>Answer is: {{ mes }}</h1>
        <button @click = "func">increase count on 1</button>
        <slot />
    </main>

    <footer class = "flex flex-row w-full bg-green-400 border-t-2 border-gray-400 items-center justify-center px-4 py-2 gap-4">
        <a href = "https://www.youtube.com/"><img src="assets/images/youtube.png" class = "w-16 h-16"></a>
        <a href = "https://github.com/"><img src="assets/images/github.png" class = "w-16 h-16"></a>
        <a href = "https://www.facebook.com/"><img src="assets/images/facebook.png " class = "w-16 h-16 bg-transparent"></a>
    </footer>
</template>

<script setup lang="ts">
import { useHead } from '#app';
import { ref} from 'vue';

// Добавляем Google Tag в head
useHead({
  script: [
    {
      async: true,
      src: 'https://www.googletagmanager.com/gtag/js?id=G-1GNCCCBG59',
    },
    {
      innerHTML: `
        window.dataLayer = window.dataLayer || [];
        function gtag(){dataLayer.push(arguments);}
        gtag('js', new Date());
        gtag('config', 'G-1GNCCCBG59');
      `,
      type: 'text/javascript',
    },
  ],
  __dangerouslyDisableSanitizersByTagID: {
    gtag: ['innerHTML'],
  },
});


let mes = ref<number>(0)

const func = ()=> {
    mes.value+=1
}
</script>

