<template>
  <Layout>
    <main>
      <header class="max-w-xl md:max-w-2xl xl:max-w-3xl mx-auto text-center px-6 pt-24">
        <h1 class="text-4xl sm:text-5xl md:text-6xl font-sans font-bold mb-1">About Me</h1>
      </header>
      <nav class="absolute top-0 left-0 z-20 mt-6 ml-6">
        <g-link
          to="/"
          class="text-gray-900 border-gray-400 text-sm border opacity-75 hover:opacity-100 rounded-full px-4 py-2 transition-opacity"
        >&larr; Home</g-link>
      </nav>
      <article
        class="max-w-xl md:max-w-2xl xl:max-w-3xl mx-auto px-6 sm:px-12 pt-8 border-b border-gray-300 pb-10 mb-16"
      >
        <div class="markdown text-lg leading-normal text-gray-700">
          <hr />
          <h2>In a word, maybe two</h2>
          <img :src="avatar" alt="avatar" />
          <p class="pt-5">
            Chibuzor Obiora, along with his Co-founder team at Jara Mobile, joined forces with Carbon (formerly Paylater) to expand loans and access to credit to SMEs.
            <br />
            <br />Before that, he worked as a full-stack software developer at Andela, a company building the next crop of technology leaders in Africa. During that spell, he spent 2½ years on the engineering team of TheMuse.com a New York based company, where he worked to make the job search process less sucky.
            <br />
            <br />Chibuzor has over five years of core software development and product management experience and has also appeared in numerous prestigious organisations like
            <a
              href="https://www.cnet.com/news/how-the-internet-is-changing-africa/"
              target="_blank"
            >CNet</a>,
            <a
              href="https://www.bbc.co.uk/sounds/play/w3csydd2"
              target="_blank"
              rel="noopener noreferrer"
            >BBC</a>, and
            <a
              href="https://www.wsj.com/video/andela-fellow-gives-inside-look-at-startup/DC663956-18BD-4C16-9035-E56E356C303C.html"
              target="_blank"
              rel="noopener noreferrer"
            >Wall Street Journal</a> to talk about all things technology.
            <br />
            <br />Chibuzor loves dogs, humans and beautiful
            <em>serverless</em> APIs.
          </p>
        </div>
      </article>
      <site-footer class="pb-8 sm:pb-10" />
    </main>
  </Layout>
</template>

<script>
import config from "~/.temp/config.js";
import SiteFooter from "@/components/Footer";

export default {
  components: {
    SiteFooter
  },
  metaInfo() {
    return {
      title: "About",
      meta: [
        {
          key: "description",
          name: "description",
          content: "Nbyodai, a tech blog."
        },

        { property: "og:type", content: "article" },
        { property: "og:title", content: "About" },
        {
          property: "og:description",
          content: "Nbyodai, a tech blog."
        },
        { property: "og:url", content: `${this.config.siteUrl}/about/` },
        { property: "og:image", content: "/images/bleda-card.png" },

        { name: "twitter:card", content: "summary_large_image" },
        { name: "twitter:title", content: "About" },
        {
          name: "twitter:description",
          content: "Nbyodai, a tech blog."
        },
        { name: "twitter:site", content: "@cossssmin" },
        { name: "twitter:creator", content: "@cossssmin" },
        { name: "twitter:image", content: "/images/bleda-card.png" }
      ]
    };
  },
  computed: {
    config() {
      return config;
    },
    avatar() {
      return "/images/authors/headshot-1.jpg";
    }
  }
};
</script>
