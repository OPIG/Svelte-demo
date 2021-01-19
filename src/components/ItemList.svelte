<script>
  import {createEventDispatcher} from 'svelte'
  export let ItemArr;
  console.log(ItemArr,'-->');

  let dispatch = createEventDispatcher()

  const delItem = (id)=>{
    console.log(id);
    dispatch('del',id)
  }
</script>

<section class="item-list-wrapper">
  <ul>
    <li>
      <span class='item-list item-list-head'>序号</span>
      <span class='item-list item-list-head'>Name</span>
      <span class='item-list item-list-head'>Age</span>
      <span class='item-list item-list-head'>Operation</span>
    </li>
  </ul>
  <ul>
    {#each ItemArr as item,index }
      <li>
        <span class='item-list sort-num'>{item.id}</span>
        <span class="item-list item-list-name">{item.name}</span>
        <span class="item-list item-list-age">{item.age}</span>
        <div class='item-list item-list-operation'>
          <button class="btn primary">Edit</button>
          <button class="btn primary" on:click={delItem(item)}>Delete</button>
        </div>
      </li>
    {/each}
  </ul>
</section>

<style>
  ul, li {
    margin: 0px;
    padding: 0px;
    outline: none;
    list-style: none;
  }

  .item-list-wrapper {
    margin-top: 60px;
  }

  .item-list-head {
    font-weight: 600;
  }

  .item-list {
    width: 20%;
    display: inline-block;
    height: 40px;
    border-bottom: 1px solid #ccc;
    line-height: 40px;
  }

  .btn {
    width: 60px;
    height: 30px;
    vertical-align: middle;
    /* line-height: 30px; */
  }

</style>