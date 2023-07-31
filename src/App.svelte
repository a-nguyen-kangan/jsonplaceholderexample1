<script>
import Post from './Post.svelte';

let postNum;

async function getPostItem(id) {
  const res = await fetch('https://jsonplaceholder.typicode.com/posts/'+id);
  const post = await res.json();
  
  console.log(post);

  if (res.ok) {
			return post;
	} else {
		throw new Error(post);
	}
 
    
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

<Post post={post} />

{:catch error}
<p style="color:red">No post data found</p>

{/await}


</main>

<style>

</style>
