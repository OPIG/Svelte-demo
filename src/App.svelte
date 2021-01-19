<script>
  import Input from './components/Input.svelte'
  import ItemList from './components/ItemList.svelte'

  let ItemArr = [
    {
      id: 1,
      name: 'zhangsan',
      age: 10
    },
    {
      id: 2,
      name: 'lisi',
      age: 20
    }
  ]
 $: t = [0,1]

  let inputVal = 'test'

  const addItem = (item) => {
    let items = {
      id: ItemArr.length + 1,
      name: inputVal,
      age: Math.ceil(Math.random()*100)
    }
    ItemArr = [...ItemArr, items]
    // ItemArr[ItemArr.length]=items
  }

  const del = (item) => {
    ItemArr= ItemArr.filter(e=>
      e.id != item.detail.id
    )
  }
</script>

<main>
  <h1>To Do List</h1>
  inputValue: {inputVal}
  <Input bind:value={inputVal} on:click={addItem(inputVal)}/>
  <ItemList {ItemArr} on:del={del}></ItemList>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>