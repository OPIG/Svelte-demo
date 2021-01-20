<script>
  let name 
  let age
  let skill =[]
  let selectVal

  const handleSubmit = () => {
    console.log(name,age,skill,selectVal);
  }

</script>

<form on:submit|preventDefault={handleSubmit}> 
  <input type="text" bind:value={name} placeholder='name' />
  <input type="text" bind:value={age} placeholder='age' />
  <div>
    <input type="checkbox" bind:group={skill} value="fighting">fighting
    <input type="checkbox" bind:group={skill} value="running">running
    <input type="checkbox" bind:group={skill} value="swimming">swimming
  </div>

  city:
  <select bind:value={selectVal}>
    <option value="shanghai">shanghai</option>
    <option value="beijing">beijing</option>
    <option value="shenzhen">shenzhen</option>
    <option value="nanjing">najing</option>
  </select>

  <button>Click me</button>
</form>