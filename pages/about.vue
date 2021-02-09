<template>
  <div id="about-page" class="page-wrapper about-page content-page">
    <site-hero
      title="About Me"
      subtitle="What I do, what I want to learn"
      image="/uploads/erik-mclean-fehsay6f3lc-unsplash.jpg"
    ></site-hero>
    <main-section theme="sidebar-right">
      <template v-slot:default>
        <div class="content">
          <h3>What I do</h3>
          <p>
            As a security analyst, my responsabilites include review security incidents, investigate for potential compromise, automate tasks, and develop dashboard visualizations.
            I also take time to focus on current industry practice and develop skills in other areas of IT.
          </p>
          <p>  
            Outside of the IT world, I enjoy tabletop games, outdoor activities, and social events.
          </p>
          <h3>What I want to learn</h3>
          <p>
            Topics that fall under the STEM category have always gained my interest.<br>
            While I beleive honing career skills is always in focus, diverisying my interest has lead me to have talents such as musicianship and refining my communicaiton.<br>
            In the meantime, these are some people that I get some unique insight from.<br>
          </p>
          <p>
            <ul>
              <li><a href="https://www.youtube.com/MichaelPennMath">Math theory from Michael Penn</a></li>
              <li><a href="https://www.youtube.com/adamneely">Music theory from Adam Neely</a></li>
              <li><a href="https://www.youtube.com/simonegiertz">Engineering ideas from Simone Giertz</a></li>
              <li><a href="https://www.youtube.com/rossmanngroup">Technology and state activism from Louis Rossmann</a></li>
              <li><a href="https://www.youtube.com/corridorcrew">Visual and special effects from the Corridor Crew</a></li>
              <li><a href="https://www.youtube.com/TomScottGo">Tom Scott on topics I didn't know that I wanted to learn</a></li>
            </ul>
          </p>
        </div>
          </template>
      <template v-slot:sidebar>
        <h3 class="subtitle is-4">
          Latest Posts
        </h3>
        <posts-grid :per-row="1" :number="2" />
      </template>
    </main-section>
  </div>
</template>
<script>
import QuoteCard from '~/components/cards/QuoteCard'
export default {
  head() {
    return {
      title: `About | ${this.$siteConfig.siteName}`
    }
  },
  components: { QuoteCard }
}
</script>
