<script>
  import {createEventDispatcher} from 'svelte'

  const dispatch = createEventDispatcher()

  const inputChange = () => {
    dispatch('changeInputVal', inputVal)
  }

  export let inputVal = ''

  
</script>

<section class="input-wrapper">
  <input type="text" bind:value = {inputVal}  on:change = {inputChange} placeholder='input anything'>
  <button class="addItem primary" on:click>Add Item</button>
</section>
<span>{inputVal}</span>

<style>
  .input-wrapper {
    width: 80%;
    height: 60px;
    margin: 0 auto;
  }

  input {
    width: 80%;
    height: 100%;
    border: 1px solid #ccc;
    outline: none;
    display: inline-block;
  }
</style>