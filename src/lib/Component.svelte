<script>
  export let data

  $: console.log('component prop changed', data)

  function action(node, data) {
    console.log('component action created')

    return {
      update(data) {
        console.log('component action updated')
      }
    }
  }
</script>

<pre use:action={data}>{JSON.stringify(data, null, 2)}</pre>