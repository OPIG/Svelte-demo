<script>
  export let buttonType = 'primary'
</script>

<button class={buttonType}>
  <slot></slot>
</button>

<style>
  button {
    border: 0;
    cursor: pointer;
    border-radius: 6px;
    padding: 8px 12px;
    font-weight: bold;
    box-shadow: 1px 2px 3px rgba(0,0,0,.2);
  }

  .primary{
    background: #d91b4d;
  }
</style>