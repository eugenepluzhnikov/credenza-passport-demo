<style lang="postcss">
  :global(html) {
    background-color: theme(colors.gray.100);
  }
</style>


<script lang="ts">
  import { onMount } from "svelte";

  import { Passport } from "@credenza-web3/passport";

  
  const passport = new Passport({
    chainId: Passport.chains.POLYGON_MUMBAI,
  });

  let isLogged = false;


  onMount(async () => {
    await passport.init();
    passport.showNavigation();
    console.log(passport);
    passport.onLogin(()=> isLogged = true);
    passport.onLogout(()=> isLogged = false);
    isLogged = passport.isLoggedIn
  });
  
</script>

{#if !isLogged }
<h1 class="text-3xl font-bold underline">Please login</h1>
{/if}

