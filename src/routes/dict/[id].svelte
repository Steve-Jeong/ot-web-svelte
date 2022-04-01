<script context="module">
  export function load({ params }) {
    const id = params.id

      return {
        props: {
          id,
        },
      };
  }
</script>

<script>
  export let id;
</script>

<h1>{ id }</h1>