<script>
  import Input from './components/Input.svelte'
  import ItemList from './components/ItemList.svelte'
  import Dialog from './components/Dialog.svelte'
  import Form from './components/form.svelte'

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
    toggleShowDialog()
    // ItemArr= ItemArr.filter(e=>
    //   e.id != item.detail.id
    // )
  }

  const toggleShowDialog = () => {
    showDialog = !showDialog
  }

  const changeInputVal = (val) => {
    // todo
    inputVal = val.detail
  }

  const update = (item) => {
    const newArr = ItemArr.map(el=>{
      if(el.id === item.detail[0].id) {
        el = item.detail[0]
      }
      return el
    })

    console.log(newArr);
   ItemArr = [ ...newArr]
  }

  let showDialog = false
</script>

<main>
  <h1>To Do List</h1>
  <input type="text" bind:value={inputVal}>
  inputValue: {inputVal}
  <Input {inputVal} on:changeInputVal={changeInputVal} on:click={addItem(inputVal)}/>
  <ItemList {ItemArr} on:del={del} on:update={update}></ItemList>
  <Dialog {showDialog} on:click={toggleShowDialog}>
    <div slot='slot-name'>
      <Form/>
    </div>
  </Dialog>
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