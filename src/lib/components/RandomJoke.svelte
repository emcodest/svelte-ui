<script lang="ts">
  import axios from "axios";
  import { onMount, onDestroy } from "svelte";
  import { Skeleton, GradientButton, Tabs, TabItem, Toast } from "flowbite-svelte";
  import { UserCircleSolid, FireOutline } from "flowbite-svelte-icons";

  // vars
  let joke: any;

  // onmount
  onMount(() => {
    FetchJoke();
  });
  // clean up
  onDestroy(() => {});

  async function FetchJoke() {
    joke = undefined;
    try {
      const mres = await axios.get(
        "https://official-joke-api.appspot.com/random_joke"
      );
      joke = mres.data;
    } catch (ex) {
      console.error(ex);
      // return false
    }
  }
</script>

<div id="joke">
  <!-- tabs -->
  <Tabs>
    <TabItem open title="Profile">
      <p class="text-sm text-gray-500 dark:text-gray-400">
        <b>Profile:</b>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
        incididunt ut labore et dolore magna aliqua.
      </p>
    </TabItem>
    <TabItem title="Settings">
      <p class="text-sm text-gray-500 dark:text-gray-400">
        <b>Settings:</b>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
        incididunt ut labore et dolore magna aliqua.
      </p>
    </TabItem>
    <TabItem title="Users">
      <p class="text-sm text-gray-500 dark:text-gray-400">
        <b>Users:</b>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
        incididunt ut labore et dolore magna aliqua.
      </p>
    </TabItem>
    <TabItem title="Dashboard">
      <p class="text-sm text-gray-500 dark:text-gray-400">
        <b>Dashboard:</b>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
        incididunt ut labore et dolore magna aliqua.
      </p>
    </TabItem>
    <TabItem disabled>
      {#snippet titleSlot()}
        <span class="text-gray-400 dark:text-gray-500">Disabled</span>
      {/snippet}
      <p class="text-sm text-gray-500 dark:text-gray-400">
        <b>Disabled:</b>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
        incididunt ut labore et dolore magna aliqua.
      </p>
    </TabItem>
  </Tabs>
  <!-- toasts -->
   <Toast>
  {#snippet icon()}
    <FireOutline class="text-primary-500 bg-primary-100 dark:bg-primary-800 dark:text-primary-200 h-6 w-6" />
  {/snippet}
  Set yourself free.
</Toast>
  <div class="card">
    {#if !joke}
      <UserCircleSolid />
      <p><b>Please wait .....</b></p>
      <Skeleton class="py-4" />
    {:else}
      <div>
        <div>ID: {joke.id}</div>
        <hr />
        <div>Type: {joke.type}</div>
        <p><b>Question ???</b></p>
        <hr />
        <div>{joke.setup}</div>
        <hr />
        <br />
        <div><b>Answer</b></div>
        <hr />

        <div>{joke.punchline}</div>
      </div>
    {/if}
    <br />
    <GradientButton color="greenToBlue" onclick={FetchJoke}
      >Get Another Joke</GradientButton
    >
  </div>
</div>

<style>
  .card {
    min-height: 200px;
    border: 2px solid red;
    padding: 15px;
    border-radius: 12px;
  }
  button {
    padding: 12px;
    background: #000;
    color: #fff;
    border: none;
    cursor: pointer;
  }
</style>
