<script>

  export let message;
  export let showModal = false;
  export let isPromo = false;
  
</script>

<style>
  .backdrop {
    width: 100%;
    height: 100%;
    position: fixed;
    z-index: 100;
    top: 0;
    left: 0;
    background-color: rgba(0,0,0, 0.8);
  }
  .modal {
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background: white;
  }
  .promo .modal {
    background: crimson;
    color: white;
  }
  h5 {
    font-size: 32px;
    margin: 0 0 20px;
  }

</style>

<!-- markup (zero or more items) goes here -->

{#if (showModal)}
  <div class="backdrop" class:promo={isPromo} on:click|self> <!-- Forward the event and the event modifier. The self event modifier activates only when the element itself is clicked. -->
    <div class="modal">
      {#if (message)}
        <h5>{message}</h5>
      {/if}
      <slot />
    </div>
  </div>
{/if}
