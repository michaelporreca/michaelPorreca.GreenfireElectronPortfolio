<template>
  <div class="hello">
    <img src="../assets/greenfire.jpg" width="600px" alt="Greenfire" />

    <h1>{{ msg }}</h1>

    <router-view/>
    <button @click="download">Download Screenshot</button>
    <div id="pdf"></div>

    <h2>QR Codes</h2>
    <div id="qr-codes">
      <div class="qr-codes-single">
        <h3>Michael Porreca</h3>
        <img src="../assets/full-name-qr.png" alt="Michael Porreca QR" class="qr" />
      </div>
      
      <div class="qr-codes-single">
        <h3>Tezos (XTZ)</h3>
        <p>${{ cryptos.XTZ.USD }}</p>
        <img src="../assets/tezos-qr.png" alt="Tezos QR" class="qr" />
      </div>
      
      <div class="qr-codes-single">
        <h3>Solana (SOL)</h3>
        <p>${{ cryptos.SOL.USD }}</p>
        <img src="../assets/solana-qr.png" alt="Solana QR" class="qr" />
      </div>
      
      <div class="qr-codes-single">
        <h3>Algorand (ALGO)</h3>
        <p>${{ cryptos.ALGO.USD }}</p>
        <img src="../assets/algorand-qr.png" alt="Algorand QR" class="qr" />
      </div>
    </div>
    
    <h2>Twitter Feeds</h2>
    <div id="twitter-feeds">
      <a class="twitter-timeline" data-tweet-limit="2" data-width="400" href="https://twitter.com/BBCAfrica?ref_src=twsrc%5Etfw">Tweets by BBCAfrica</a> <script type="application/javascript" async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> <a class="twitter-timeline" data-tweet-limit="2" data-width="400" href="https://twitter.com/ethereum?ref_src=twsrc%5Etfw">Tweets by ethereum</a> <script type="application/javascript" async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
    </div>

    <h2>Social Links</h2>
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
import axios from 'axios'
import html2canvas from 'html2canvas'
import * as JsPDF from 'jspdf'

export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data: () => ({
    cryptos: [],
    errors: []
  }),

  created () {
    axios.get('https://min-api.cryptocompare.com/data/pricemulti?fsyms=XTZ,SOL,ALGO&tsyms=USD')
      .then(response => {
        this.cryptos = response.data
        console.log(response)
      })
      .catch(e => {
        this.errors.push(e)
      })
  },
  methods: {
    download () {
      html2canvas(document.querySelector('.hello'), {imageTimeout: 5000, useCORS: true}).then(canvas => {
        document.getElementById('pdf').appendChild(canvas)
        let img = canvas.toDataURL('image/png')
        let pdf = new JsPDF('portrait', 'mm', 'a4')
        pdf.addImage(img, 'JPEG', 5, 5, 200, 287)
        pdf.save('relatorio-remoto.pdf')
        document.getElementById('pdf').innerHTML = ''
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h2 {
  margin: 40px 0 40px;
  padding: 25px;
  border-bottom: 1px solid green;
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
  color: #000;
  background-color: #B2D2A4;
  border: 1px solid #1A4314;
  padding: 10px;
  border-radius: 10px;
  text-decoration: none;
}
#qr-codes, #twitter-feeds {
  display: flex;
  justify-content: space-evenly;
}
.qr-codes-single {
  padding: 50px;
  background-color: #F3F3F3;
  border-radius: 20px;
  border: 1px solid #ccc;
}
.qr {
  width: 100px;
  height: 100px;
}
button {
  background-color: #B2D2A4;
  border: 1px solid #1A4314;
  padding: 10px;
  border-radius: 10px;
}
</style>
