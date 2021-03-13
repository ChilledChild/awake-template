<template>
  <div id="contact-page" class="page-wrapper contact-page content-page">
    <site-hero
      title="Contact Me"
      subtitle=""
      image="/uploads/contact-hero.jpg"
    ></site-hero>
    <main-section theme="sidebar-right">
      <template v-slot:default>
        <div class="tile is-ancestor">
          <div class="tile is-parent">
            <article class="tile is-child box">
              <p class="title">
                Hello!
              </p>
              <p class="subtitle">
                What can I do for you?
              </p>
              <figure class="image is-1by1 ">
                <opti-image
                  :src="require('~/assets/uploads/profile-cut.jpg').src"
                  :srcset="
                    require('~/assets/uploads/profile-cut.jpg').srcSet
                  "
                />
              </figure>
              <br />
              <div class="content">
                <p>
                  <strong>
                    Cyber Security Analyst
                  </strong>
                </p>
                <p>
                  <a href="https://www.linkedin.com/in/dannychild/">Linkedin</a>
                </p>
                <p>
                  <a href="https://twitter.com/_chilledchild">Twitter</a>
                </p>
                <p>
                  <a href="https://github.com/ChilledChild">Github</a>
                </p>
              </div>
            </article>
          </div>
          <div class="tile is-parent is-8">
            <article class="tile is-child box">
              <contact-form />
            </article>
          </div>
        </div>
      </template>
      <template v-slot:sidebar>
        <h3 class="subtitle is-4">
          Latest Posts
        </h3>
        <!-- Latest Posts -->
        <posts-grid :per-row="1" :number="2" />
      </template>
    </main-section>
  </div>
</template>
<script>
import ContactForm from '~/components/ContactForm.vue'
export default {
  head() {
    return {
      title: `Contact | ${this.$siteConfig.siteName}`
    }
  },
  components: { ContactForm }
}
</script>
