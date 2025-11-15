<script lang="ts">
    import Button from '$lib/components/Button.svelte';
    import { onMount, onDestroy } from 'svelte';
    let name = "";
    let count = 0
    let select_name = "1"
    let color = "red"
    let num1 = 0, num2 = 0
    let result : string | number = ""
    let inputBox : HTMLInputElement
    // reactive statement
    $:  console.log({name})
      $: addNumber(num1, num2)
    onMount( 
        () => {
         //  alert("am here ...") 
           inputBox.focus()
           return () => {
                console.log('Component destroyed!');
            };
        })
        onDestroy(() => {
            console.log("component destroyed")
        })
    // fxn to increment cnt
    function increment() {
        count += 1
    }
    function MyName() {
       // alert(select_name)
    }
    function focusInput() {
        inputBox.focus()
    }
    function addNumber(a: number, b: number) {
      
      console.log("answer is: ", a + b)
      result = a +b
    }
</script>
<div id = "wrapper">

    <div class:red = {color == "red"} class:blue = {color == "blue"}  style = "height: 60px; border: 1px solid red">
        <Button myname = {name} />

    </div>
    Hello <strong>{name}!</strong> and count is {count}
    <div>
        <h2>Lets Add button</h2>
        <h1>CNT: {count}</h1>
        <hr />
        <p><b>Name of Person</b></p>
        <input type = "text" bind:value={name} />
        <button on:click={increment}>Inc Name</button>
        <hr />
        <select bind:value={color}>
            
            <option value = "red">red</option>
            <option value = "blue">blue</option>
        </select>
        <hr />
        <h4>Focus here</h4>
        <input bind:this={inputBox} type = "text" />
        <hr />
        <button on:click={focusInput}>Focus</button>
        <hr />
        <input bind:value={num1} type = "number" />
        <input bind:value={num2} type = "number" />
        {#if result}
        <p><b>Ans: </b> {result}</p>
        {/if}
        <hr />
        <h3>Repeat ITEMS</h3>
        <ul>
            {#each ["Emma", "Ruth"] as name }
            <li>List 1 - {name}</li>
            {:else}
            <p><b>Nobody</b></p>
            {/each}
        </ul>

    </div>
</div>
<style>
    .red {
        background: red;
    }
    .blue{
        background: blue;
    }
    #wrapper {
    font-family: Arial, sans-serif;
    text-align: center;
    padding: 2rem;
    max-width: 70%;
    margin: 0 auto;
    border: 1px solid #ddd;
    border-radius: 10px;
  }
  input {
    padding: 0.5rem;
    font-size: 1rem;
    width: 80%;
    margin: 1rem 0;
  }
  button {
    padding: 0.5rem 1rem;
    font-size: 1rem;
    background: #ff3e00;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  button:hover {
    background: #ff6b35;
  }
</style>
