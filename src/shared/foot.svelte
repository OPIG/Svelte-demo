<script>
  const current = new Date()
  $: time = current.getFullYear() + '-' + current.getMonth() + 1 + '-' + current.getDate()
  console.log(current.getFullYear());

</script>
<footer>
  &copy; Copyright Atom Yuan {time}
</footer>

<style>
  footer{
    text-align: center;
  }
</style>