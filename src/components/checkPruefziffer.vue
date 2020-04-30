<template>
  <v-form ref="form" v-model="valid">
    <v-text-field
      v-model="serialNumber"
      :rules="serialNumberRules"
      label="Seriennummer"
      required
      :counter="12"
    ></v-text-field>
    <v-btn
      color="success"
      :disabled="nummeredSN == ''"
      class="mr-2"
      @click="checkPruefziffer"
      >Check Prüfziffer</v-btn
    >
    <v-btn
      color="info"
      @click="positionImAlphabet"
      class="mr-2"
      :disabled="!valid"
      >Umwandeln von Buchstaben in Zahlen</v-btn
    >
    <v-btn color="error" @click="reset">Reset Form</v-btn>

    <v-dialog v-model="successdialog">
      <v-card>
        <v-alert type="success" class="mb-0">
          Prüfziffer ist korrekt!
        </v-alert>
      </v-card>
    </v-dialog>
    <v-dialog v-model="failedDialog">
      <v-card>
        <v-alert type="error" class="mb-0">
          Prüfziffer ist nicht korrekt!
        </v-alert>
      </v-card>
    </v-dialog>
  </v-form>
</template>

<script>
export default {
  name: "checkPruefziffer",
  data: () => ({
    valid: true,
    serialNumber: "",
    nummeredSN: "",
    serialNumberRules: [
      v => !!v || "Seriennummer is required",
      v => (v && v.length == 12) || "Seriennummer muss 12 Zeichen lang sein",
    ],
    initialvalue: 0,
    final: 0,
    quersumme: 0,
    rest: 0,
    checkSN: false,
    successdialog: false,
    failedDialog: false
  }),
  methods: {
    reset() {
      this.$refs.form.reset();
      this.serialNumber = "";
      this.nummeredSN = "";
      this.final = 0;
      this.quersumme = 0;
      this.rest = 0;
    },
    positionImAlphabet() {
      this.nummeredSN = this.serialNumber
        .toUpperCase()
        .split("")
        .map(this.charToDigit);
    },
    charToDigit(letter) {
      const alphabet = [
        "A",
        "B",
        "C",
        "D",
        "E",
        "F",
        "G",
        "H",
        "I",
        "J",
        "K",
        "L",
        "M",
        "N",
        "O",
        "P",
        "Q",
        "R",
        "S",
        "T",
        "U",
        "V",
        "W",
        "X",
        "Y",
        "Z"
      ];
      return parseInt(letter, 10) || alphabet.indexOf(letter) + 1;
    },
    checkPruefziffer() {
      this.quersumme =
        this.nummeredSN[0] +
        this.nummeredSN[1] +
        this.nummeredSN[2] +
        this.nummeredSN[3] +
        this.nummeredSN[4] +
        this.nummeredSN[5] +
        this.nummeredSN[6] +
        this.nummeredSN[7] +
        this.nummeredSN[8] +
        this.nummeredSN[9] +
        this.nummeredSN[10];
      this.rest = this.quersumme % 9;
      this.final = 7 - this.rest;
      if (this.final == this.nummeredSN[11]) {
        this.checkSN = true;
        this.successdialog = true;
      }
      else {
        this.failedDialog = true;
      }
    }
  }
};
</script>

<style scoped></style>
