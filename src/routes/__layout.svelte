<script context="module">
  export async function load() {
    console.log('load')
    return {
      props: {
        data: { name: 'One', values: [1, 2, 3, 4, 5] }
      },
    }
  }
</script>

<script>
  import Component from '$lib/Component.svelte'

  export let data

  $: console.log('layout prop changed', data)

  function action(node, data) {
    console.log('layout action created')

    return {
      update(data) {
        console.log('layout action updated')
      }
    }
  }
</script>

<h1>__Layout Props</h1>

<nav>
  <a href="/">Home</a>
  <a href="/about">About</a>
</nav>

<slot></slot>

{#each data.values as value}
  <a href="?id={value}">{value}</a>
{/each}

<div use:action={data}><Component {data} /></div>

<style>
  a {
    padding: 4px;
  }
</style>