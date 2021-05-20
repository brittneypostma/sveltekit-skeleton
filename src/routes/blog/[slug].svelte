<!-- holds the data received from the endpoint, generates the route /blog/[post] in this case [post] is the name of each post-->
<script context="module">
  // statically generates page
  // export const prerender = true

  export async function load({ page, fetch }) {
    const response = await fetch(`./posts/${page.params.slug}.md`)
    console.log(response)
    return {
      props: {
        post: response.default,
      },
    }
  }
</script>

<script>
  export let post
  // console.log(post)
</script>

<article>
  {post}
</article>
