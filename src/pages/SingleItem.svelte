<script>
import Comment from "./../components/Comment.svelte"
export let id;
let promise = fetch(`https://node-hnapi.herokuapp.com/item/${id}`).then(res => res.json());
</script>

{#await promise}
    <h2>Loading...</h2>
    {:then data}
   <h2>{data.title}</h2>
   <Comment comment={data} />
{/await}

