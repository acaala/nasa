<script lang="ts">  
    import { API_KEY } from '$lib/Env.js'
    import Pod from '$lib/Pod.svelte';
    import { onMount } from 'svelte';
    import type { IData } from 'types'
 
    let pod = {} as IData
    $: images = []
    let userInput: string

    async function fetchPod() {
      pod = await fetch(`https://api.nasa.gov/planetary/apod?api_key=${API_KEY}`).then(r => r.json())
    }


   const fetchUserSearch = async () => {
     const response = await fetch(`https://images-api.nasa.gov/search?q=
     ${userInput}`).then(r => r.json())
    
     for(let key in response.collection.items){
      if (images.length < 10){
        images.push(response.collection.items[key])
      }
     }

     console.log('Images after search', images)
   } 

  

    onMount(fetchPod)
</script>

<svelte:head>
    <style>
        body {
          background: rgb(32, 32, 35);
          font-family: 'Poppins';
        }
      </style>
  <link href="https://fonts.googleapis.com/css?family=Poppins" rel="stylesheet">
</svelte:head>
   

<h1>Nasa-API</h1>
<h3>Picture of the day</h3>
  <Pod {...pod} />

  <div>
  <h3>Search For an image</h3>
  <input type="text" bind:value="{userInput}">
  <button on:click="{fetchUserSearch}">Search</button>
   
    {#each images as image, i}
      <p>{i}</p>
    <p>{image.href}</p>
    {/each}
</div>

<style>
h1 {
  text-align: center;
  color: white;
}

h3 {
  text-align: center;
  color: rgb(165, 165, 165);
}
div {
  width: 50%;
  margin: 2.5rem auto;
}
input {
  width: 100%;
}

</style>