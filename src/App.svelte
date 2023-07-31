<script>

let postNum;

async function getPostItem(id) {
  const res = await fetch('https://jsonplaceholder.typicode.com/posts/'+id);
  const post = await res.json();
  
  console.log(post);

  return post;
    
}

function handleClick() {
  promise = getPostItem(postNum);
}

let promise = getPostItem();

</script>

<input type='number' bind:value={postNum}/>
<button on:click={handleClick}>Get Post</button>

<main>

{#await promise}
<p>Waiting...</p>

{:then post}

<h2>{post.title}</h2>
<p>{post.body}<p>

{/await}


</main>

<style>

</style>
