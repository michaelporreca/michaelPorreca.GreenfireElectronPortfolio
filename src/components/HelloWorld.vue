<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <h3>QR Codes</h3>
    <div id="qr-codes">
      <img src="../assets/full-name-qr.png" alt="Michael Porreca QR" class="qr" /> <img src="../assets/tezos-qr.png" alt="Tezos QR" class="qr" /> <img src="../assets/solana-qr.png" alt="Solana QR" class="qr" /> <img src="../assets/algorand-qr.png" alt="Algorand QR" class="qr" />
    </div>
    
    <h3>Twitter Feeds</h3>
    <div id="twitter-feeds">
      <a class="twitter-timeline" data-tweet-limit="2" data-width="400" href="https://twitter.com/BBCAfrica?ref_src=twsrc%5Etfw">Tweets by BBCAfrica</a> <script type="application/javascript" async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> <a class="twitter-timeline" data-tweet-limit="2" data-width="400" href="https://twitter.com/ethereum?ref_src=twsrc%5Etfw">Tweets by ethereum</a> <script type="application/javascript" async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
    </div>

    <h3>Social Links</h3>
    <div id="twitter-feeds">
      <a href="https://github.com/michaelporreca" target="_blank" alt="">GitHub</a>
      <a href="https://www.linkedin.com/in/michael-porreca/" target="_blank" alt="">LinkedIn</a>
      <a href="mailto:michaelporreca@gmail.com" target="_blank" alt="">Email</a>
      <a href="https://michaelporreca.dev/downloads/MichaelPorrecaResume.pdf" target="_blank" alt="">Resume</a>
      <a href="http://michaelporreca.dev" target="_blank" alt="">Website</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 40px;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
#qr-codes, #twitter-feeds {
  display: flex;
  justify-content: space-evenly;
}
.qr {
  width: 100px;
  height: 100px;
}
</style>
