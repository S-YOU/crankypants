<template lang="pug">
  article.post
    .container(v-if="editing")
      post-form(
        :title="post.title"
        :body="post.body"
        cancel="true"
        @cancel="cancelEditing"
        @submit="updatePost")

    .container(v-else)
      h2(v-if="post.title") {{ post.title }}
      .post-body(
        ref="post_body"
        v-html="post.body_html"
        v-prism)

      footer
        button(@click="startEditing") edit
        button(@click="deletePost") delete
        span.post-meta {{ postedWhen }}
</template>

<script lang="coffee">
  import PostForm from './PostForm'
  import format from 'date-fns/format'

  export default
    components: { PostForm }
    props: ['post']

    computed:
      postedWhen: ->
        format @post.created_at, "MMM Do, HH:mm"

    data: ->
      editing: false

      # I have no idea, but it makes v-prism work
      prism: true
      v: true

    methods:
      startEditing: ->
        @editing = true

      cancelEditing: ->
        @editing = false

      updatePost: ({ title, body }) ->
        @$store
          .dispatch 'updatePost', { id: @post.id, title, body }
          .then => @editing = false

      deletePost: ->
        if confirm 'Are you sure? There is no undo!'
          @$store.dispatch 'deletePost', @post
</script>
