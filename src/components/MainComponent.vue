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
