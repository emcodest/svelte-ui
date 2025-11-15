<script lang="ts">
  import {onMount} from "svelte"
  import {
    Button,
    Alert,
    Skeleton,
    ImagePlaceholder,
    BottomNav,
    BottomNavItem,
    Heading,
    Toggle,
    Card,
    Modal,
    P,
  } from "flowbite-svelte";

  import {
    HomeSolid,
    WalletSolid,
    AdjustmentsVerticalOutline,
    UserCircleSolid,
  } from "flowbite-svelte-icons";
  import { page } from "$app/state";
   import { Toaster, toast } from 'svelte-sonner';
  let activeUrl = $derived(page.url.pathname);
  let defaultModal = $state(false);



</script>

<div class="p-5">
  <h1>We are going to use framework here ..</h1>
  <p><b>Using flowbite - svelte</b></p>
  <!-- toaster -->
   <Toaster position="top-right" />

<Button 
  color="green" 
  onclick={() => toast.success('Success!', {
    description: 'Your action completed successfully',
    style: 'background: #10b981; color: white !important',
    class: "green-toast"
  })}
>
  Show success
</Button>

<Button 
  onclick={() => toast.error('Error!', {
    description: 'Your action completed successfully',
    style: 'background: red; color: white !important',
    class: "red-toast"
  })}>
  Show error
</Button>
  <hr />
  <div>
    <h3>This is a button</h3>
    <hr />
    <br />
    <Button>Submit Now</Button>

    <br />
    <br />
    <hr />
  </div>
  <!-- alerts -->
  <div>
    <Heading>Alerts</Heading>
    <Toggle>Toggle me</Toggle>
    <div class="p-8">
      <Alert color="blue">
        <span class="font-medium">Info alert!</span>
        Change a few things up and try submitting again.
      </Alert>
    </div>
  </div>
  <!-- CARD -->
  <div>
    <h3>Card</h3>
    <Card size="lg" class="p-4 text-center sm:p-8 md:p-10">
      <h5 class="mb-2 text-3xl font-bold text-gray-900 dark:text-white">
        Work fast from anywhere
      </h5>
      <p class="mb-5 text-base text-gray-500 sm:text-lg dark:text-gray-400">
        Stay up to date and move work forward with Flowbite on iOS & Android.
        Download the app today.
      </p>
      <div
        class="items-center justify-center space-y-4 sm:flex sm:space-y-0 sm:space-x-4 rtl:space-x-reverse"
      >
        <Button>Download it</Button>
        <Button>Get it on</Button>
      </div>
    </Card>
  </div>
  <!-- MODAL -->
  <Button onclick={() => (defaultModal = true)}>Default modal</Button>
  <Modal
    title="Terms of Service"
    form
    bind:open={defaultModal}
    onaction={({ action }) => alert(`Handle "${action}"`)}
  >
    <P
      >With less than a month to go before the European Union enacts new
      consumer privacy laws for its citizens, companies around the world are
      updating their terms of service agreements to comply.</P
    >
    <P>
      The European Union’s General Data Protection Regulation (G.D.P.R.) goes
      into effect on May 25 and is meant to ensure a common set of data rights
      in the European Union. It requires organizations to notify users as soon
      as possible of high-risk data breaches that could personally affect them.
    </P>

    {#snippet footer()}
      <Button type="submit" value="success">I accept</Button>
      <Button type="submit" value="decline" color="alternative">Decline</Button>
    {/snippet}
  </Modal>
  <!-- Bottom nav -->
  <!-- <Skeleton class="py-4" /> -->
  <!-- <ImagePlaceholder class="pb-20" /> -->

  <!-- <BottomNav
    {activeUrl}
    position="absolute"
    classes={{ inner: "grid-cols-4" }}
    activeClass="font-bold text-green-500 hover:text-green-900 dark:hover:text-green-700 dark:text-green-300"
  >
    <BottomNavItem btnName="Home" href="/">
      <HomeSolid />
    </BottomNavItem>
    <BottomNavItem btnName="Quickstart" href="/docs/pages/quickstart">
      <WalletSolid />
    </BottomNavItem>
    <BottomNavItem
      btnName="BottomNav"
      href="/docs/components/bottom-navigation"
    >
      <AdjustmentsVerticalOutline />
    </BottomNavItem>
    <BottomNavItem btnName="Accordion" href="/docs/components/accordion">
      <UserCircleSolid />
    </BottomNavItem>
  </BottomNav> -->
</div>
<style>
   :global(.green-toast) {
    background: #10b981 !important;
  }
  :global(.green-toast *) {
    color: #fff !important;
  }
   :global(.red-toast) {
    background: red !important;
  }
  :global(.red-toast *) {
    color: #fff !important;
  }
</style>
