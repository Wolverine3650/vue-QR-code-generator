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
  cursor: pointer;
}
.button {
 padding: 1.3em 3em;
 font-size: 12px;
 text-transform: uppercase;
 letter-spacing: 2.5px;
 font-weight: 500;
 color: #000;
 background-color: #fff;
 border: none;
 border-radius: 45px;
 box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.1);
 transition: all 0.3s ease 0s;
 cursor: pointer;
 outline: none;
}

.button:hover {
 background-color: #2EE59D;
 box-shadow: 0px 15px 20px rgba(46, 229, 157, 0.4);
 color: #fff;
 transform: translateY(-7px);
}

.button:active {
 transform: translateY(-1px);
}
</style>
