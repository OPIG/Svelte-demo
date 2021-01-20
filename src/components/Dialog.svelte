<script>
  export let showDialog = false
</script>

{#if showDialog}
<section class="dialog-wrapper" on:click|self>
  <div class="dialog-content">
    <h3>Do you want to delete this item</h3>
    <button on:click|self>No</button>
    <button>Yes</button>
    <slot name='slot-name'></slot>
  </div>
  
</section>
{/if}

<style>
  .dialog-wrapper {
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,.8);
    position: fixed;
    top: 0;
    left: 0;
    z-index: 2;
  }
  .dialog-content {
    width: 500px;
    height: 300px;
    background: #fff;
    position: relative;
    top: 50%;
    left: 50%;
    margin: -150px 0 0 -250px;
    box-sizing: border-box;
    padding: 20px;
  }
</style>