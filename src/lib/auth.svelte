<script>
  let user = { loggedIn: false }

  function toggle() {
    user.loggedIn = !user.loggedIn
  }
</script>

<div>
  {#if user.loggedIn}
    <button on:click={toggle}> Log out </button>
  {:else}
    <button on:click={toggle}> Log in </button>
  {/if}
</div>

<style>
  button {
    box-shadow: var(--box-shadow);
  }

  button:hover {
    --box-shadow: 0px 0px 4px rgba(0, 0, 0, 0.5);
  }
</style>
