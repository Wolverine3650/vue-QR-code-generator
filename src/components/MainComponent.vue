<template>
  <div>
    <Header />
    <div>
      <input
        type="text"
        name="Generate"
        placeholder="Enter Text Here"
        v-model="sequenceToGenerate"
      />
    </div>
    <div>
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
    </div>
    <div v-show="showSpinner">
      <img src="../assets/Hourglass.gif" width="150" height="150" />
    </div>
    <div v-show="showQR">
      <qrcode-vue :value="value" :size="size" level="H" />
    </div>
  </div>
</template>

<script>
import Header from "../components/header/Header.vue";
import QrcodeVue from "qrcode.vue";

export default {
  data() {
    return {
      value: "",
      size: 300,
      sequenceToGenerate: "",
      showQR: false,
      nodata: false,
      showSpinner: false,
      beforeKeyUpSequenceToGenerate: "",
    };
  },
  components: { Header, QrcodeVue },
  name: "MainComponent",
  methods: {
    GenerateQR() {
      this.showQR = false;
      if (this.sequenceToGenerate == "") {
        this.showQR = false;
        this.nodata = true;
      } else {
        this.showSpinner = true;
        setTimeout(() => {
          this.showQR = true;
          this.value = this.sequenceToGenerate;
          this.showSpinner = false;
        }, 2000);
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
