<script>

let postNum;

async function getPostItem(id) {
  const res = await fetch('https://jsonplaceholder.typicode.com/posts/'+id);
  const post = await res.json();
  
  console.log(post);

  return post;
    
}

async function getAllPosts() {
  const res = await fetch('https://jsonplaceholder.typicode.com/posts');
  const posts = await res.json();

  console.log(posts);

  return posts;
}

function handleClick() {
  promise = getPostItem(postNum);
}

let promise = getAllPosts();

</script>

<main>

{#await promise}
<p>Waiting...</p>

{:then posts}

  {#each posts as post}
    <a href="https://jsonplaceholder.typicode.com/posts/{post.id}"><h2>{post.id}: {post.title}</h2></a>
  {/each}

{/await}


</main>

<style>

</style>
