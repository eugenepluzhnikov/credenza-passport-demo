<script lang="ts">
  import { onMount } from "svelte";

  import { Passport } from "@credenza-web3/passport";


  const passport = new Passport({
    chainId: Passport.chains.POLYGON_MUMBAI,
  });

  onMount(async () => {
    await passport.init();
    passport.showNavigation();
  });
</script>

<h1 class="text-3xl font-bold underline">Hello world!</h1>

<style lang="postcss">
  :global(html) {
    background-color: theme(colors.gray.100);
  }
</style>
