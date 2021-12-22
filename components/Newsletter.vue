<template>
  <SimpleNewsletter v-slot="{ slotProps }">
    <div class="newsletter__wrap">
      <div class="newsletter__title">{{ slotProps.title }}</div>
      <div class="newsletter__content">{{ slotProps.content }}</div>
      <div id="firewall-rules"
                style="display: none" 
                class="sk-widget"
                data-width="600"
                data-course-id="1"
                data-client-id="86bfa9f2-6238-4241-83be-fd961e72b996">
            </div>
      <div class="newsletter__fields">
        <input
          v-model="slotProps.mail"
          class="newsletter__input"
          type="email"
          name="email"
          aria-label="Email"
          placeholder="Email"
          required
          autocapitalize="off"
          autocorrect="off"
          data-cy="email"
        />
        <button type="submit" class="newsletter__button" data-cy="submit">
          {{ slotProps.submitText }}
        </button>
      </div>
    </div>
  </SimpleNewsletter>
</template>

<script>
import SimpleNewsletter from 'vuepress-plugin-mailchimp/src/components/SimpleNewsletter'
export default {
  components: { SimpleNewsletter },
}
</script>

<script>
export default {
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
};
</script>

<style type="text/css">
      .sk-widget .sk-text {
          font-size: 1.5rem;
          font-weight: 400;
      }
  </style>


<style lang="stylus">
.newsletter
  .newsletter &__wrap
    max-width none
    padding: 1.8rem 2.3rem 3rem
    background: #e5f5f0

  .newsletter &__fields
    display grid
    grid-template-columns 2fr 1fr
    grid-gap 10px

  .newsletter &__input
    margin-bottom 0

  .newsletter &__content
    margin-top:0

  .newsletter &__button
    transition box-shadow 0.2s ease, transform 0.2s ease

    &:hover
      box-shadow 1px 1px 5px rgba(0, 0, 0, 0.6)
      transform translateY(-2px)

@media (max-width: $MQMobile)
  .newsletter
    .newsletter &__fields
      display block

    .newsletter &__input
      margin-bottom 10px
</style>
