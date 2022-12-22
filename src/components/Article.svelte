<script lang="ts">
  export let title: string = "title";
  export let author: string = "Peter Yuan";
  export let authorLabel: string = "Written by";
  export let leading: string = "this is an article";
  export let content: string = "hello world";
  export let readMoreText: string = "Read More";
</script>

<article class="article">
  <h1 class="article-title"><a href="">{title}</a></h1>
  <p class="article-meta">{authorLabel} <a href="#">{author}</a></p>
  <p class="text-lead">{leading}</p>
  <p>{content}</p>
  <div class="row">
    <button>{readMoreText}</button>
  </div>
</article>
