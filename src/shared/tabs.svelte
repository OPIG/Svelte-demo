<script>
  import { createEventDispatcher } from 'svelte'
  export let navItems = []
  export let currentNav

  const dispatch  = createEventDispatcher()

  const clickNav = (item) => {
    dispatch('clickNav', item)
  }
</script>

<ul class="item-nav">
  {#each navItems as nav}
    <li class:active={currentNav === nav} on:click={()=>{clickNav(nav)}}> { nav } </li>
  {/each}
</ul>

<style>
  .item-nav {
    display: flex;
    flex-flow: row nowrap;
    justify-content: center;
    width: 100%;
    margin-bottom: 20px;
  }

  li {
    margin: 0 10px;
    color: #000;
    font-family: '微软雅黑';
  }
  li:hover {
    color: #900;
    cursor: pointer;
  }

  li.active {
    color: #900;
    border-bottom: 2px solid #900;
  }
</style>