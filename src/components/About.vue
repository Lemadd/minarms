<template>
  <div class="about">
    <h1>What is a Crypto-Currency?</h1>
    <p>
      It's a digital currency in which encryption techniques are used to regulate the generation of units of currency and verify the transfer of funds, operating independently of a central bank.
    </p>
    <vue-markdown :source="source"></vue-markdown>
  </div>
</template>

<script>
import VueMarkdown from 'vue-markdown' // production
  import testmd from './test.md'
  export default {
    name: "About",
    data() {
      return {
        source: "# Hello World \n ! Just testing... \n ## Simple Code Block \n ```html <template>  <div>Nothing happends</div></template>```"
      }
    },
    components: {
    VueMarkdown
    }/*,
    mounted() {
      setInterval(() => {
        this.source = "#### Table 2 \n aaaa";
      }, 1000);
    }*/
  }
</script>
