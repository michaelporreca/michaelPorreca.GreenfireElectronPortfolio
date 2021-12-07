<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h3>QR Codes</h3>
    <div id="qr-codes">
      <img src="../assets/full-name-qr.png" alt="Michael Porreca QR" class="qr" /> <img src="../assets/tezos-qr.png" alt="Tezos QR" class="qr" /> <img src="../assets/solana-qr.png" alt="Solana QR" class="qr" /> <img src="../assets/algorand-qr.png" alt="Algorand QR" class="qr" />
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
