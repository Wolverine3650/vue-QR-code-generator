<template>
  <div>
    <Header />
    <input
      type="text"
      name="Generate"
      placeholder="Enter Text Here"
      v-model="sequenceToGenerate"
    />
    <br />
    <input
      type="button"
      class="button"
      value="Generate QR code"
      @click="GenerateQR()"
    />
    &nbsp;
    <input type="button" class="button" value="Reset" @click="reset()" />
    <br />
    <br />
    <qrcode-vue v-show="showQR" :value="value" :size="size" level="H" />
  </div>
</template>

<script>
import Header from "../components/header/Header.vue";
import QrcodeVue from "qrcode.vue";

export default {
  data() {
    return {
      value: "",
      sequenceToGenerate: "",
      showQR: false,
      nodata:false,
      beforeKeyUpSequenceToGenerate: "",
      size: 300,
    };
  },
  components: { Header, QrcodeVue },
  name: "MainComponent",
  methods: {
    GenerateQR() {
      if (this.sequenceToGenerate == "") {
        this.showQR = false;
        this.nodata = true;
      } else {
        this.showQR = true;
        this.value = this.sequenceToGenerate;
        console.log("clicked");
      }
    },
    reset() {
      this.value = "";
      (this.sequenceToGenerate = ""), (this.showQR = false);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input[type="text"] {
  border-radius: 15px 15px 15px 15px;
  padding-left: 40px;
  width: 50%;
  font-size: 25px;
  padding: 12px 20px;
  margin: 8px 0;
}
.button {
  display: inline-block;
  padding: 15px 25px;
  font-size: 24px;
  cursor: pointer;
  text-align: center;
  text-decoration: none;
  outline: none;
  color: #fff;
  background-color: #02485a;
  border: none;
  border-radius: 15px;
  box-shadow: 0 9px #999;
}

.button:hover {
  background-color: #02485a;
}

.button:active {
  background-color: #02485a;
  box-shadow: 0 5px #666;
  transform: translateY(4px);
}
</style>
