<template>
<div id="vuepress-theme-blog__post-layout">

<article
class="vuepress-blog-theme-content"
itemscope
itemtype="https://schema.org/BlogPosting"
>

<div class="row justify-content-center">
  <div class="col-md-8">
  <header>

  <span class="text-muted"><PostMeta  :date="$frontmatter.date" /></span>
  <h1 class="article-head mt-3" itemprop="name headline">
  {{ $frontmatter.title }}
  </h1>
  <p class="lead">{{ $frontmatter.description }}</p>

  <Avatar />

  </header>
  </div>
</div>

<!--div class="row justify-content-center text-center mt-4 mb-40"-->
<div class="row justify-content-center">
  <div class="col-md-8">

    <!--img class="featuredimg" :src="$frontmatter.featuredimg"-->
  </div>
</div>

<div id="firewall-rules"
                    class="sk-widget"
                    data-width="600"
                    data-course-id="3"
                    data-client-id="86bfa9f2-6238-4241-83be-fd961e72b996">
                </div>

<div class="row justify-content-center">
  <div class="col-md-8">
  <Content  itemprop="articleBody" />


  <PostMeta
  :tags="$frontmatter.tags"/>

  </div>
</div>

</article>

<div class="row justify-content-center">
  <div class="col-md-9">
    <Newsletter v-if="$service.email.enabled" />
    <Comment />
  </div>
</div>

<Toc />
</div>
</template>

<script>
import Toc from '@theme/components/Toc.vue'
import PostMeta from '@theme/components/PostMeta.vue'
import Avatar from '@theme/components/Avatar.vue'
import { Comment } from '@vuepress/plugin-blog/lib/client/components'

export default {
  components: {
    Toc,
    PostMeta,
    Avatar,
    Comment,
    Newsletter: () => import('@theme/components/Newsletter.vue'),
  },
  mounted() {
    const plugin = document.createElement("script");
    plugin.setAttribute(
      "src",
      "https://microlearn.azurewebsites.net/js/bundle/runtime.js"
    );
    plugin.setAttribute(
      "data-id",
      "sk-runtime"
    );
    plugin.async = true;
    document.head.appendChild(plugin);
  }

}
</script>

<style lang="stylus" scoped>
@import url('https://fonts.googleapis.com/css?family=Merriweather:400,400i,700&display=swap')
</style>

<style type="text/css">
      .sk-widget .sk-text {
          font-size: 1.5rem;
          font-weight: 400;
      }
  </style>