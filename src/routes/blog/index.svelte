<!-- root of the blog route, generates the route /blog, list all blog posts here
npx svelte-add mdsvex -->
<script context="module">
  //statically generate page
  export const prerender = true

  const posts = Object.entries(import.meta.globEager('./posts/*.md')).map(
    ([, post]) => post.metadata
  )
  // .filter(post => !post.hidden)
  // .sort((a, b) => (a.created < b.created ? 1 : -1))

  export const load = async () => {
    return {
      props: {
        posts,
      },
    }
  }
</script>

<script>
  export let posts
</script>

<h1>Blog</h1>
<ul class="list-none">
  {#each posts as { title, slug }}
    <li class="list-none">
      <a class="space-y-3 text-blue-500" rel="prefetch" href="blog/{slug}">
        <h2>
          {title}
        </h2>
      </a>
    </li>
  {/each}
</ul>
