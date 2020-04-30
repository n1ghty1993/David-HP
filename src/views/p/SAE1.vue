<template>
  <div>
    <v-container fluid>
      <div class="display-3 text-center mb-3">
        SAE ÜBUNG 1
      </div>
      <div class="mb-3">
        <h3>
          Für die Kassen im Eingangsbereich eines Freizeitbades werden
          Geldscheinprüfgeräte angeschafft. Diese Geräte können über eine
          Schnittstelle mit zusätzlichen Funktionen erweitert werden. Es gibt
          bereits die Methode „positionImAlphabet", die die Position eines
          Buchstabens im Alphabet als ganze Zahl zurückgibt mit:
        </h3>
        <p><b>Eingabe:</b> Buchstabe b</p>
        <p><b>Ausgabe:</b> ganze Zahl</p>
      </div>
      <div class="mb-3">
        <h3>
          Programmieren Sie die Methode „pruefeKontrollnummer", die zurückgibt,
          ob die Seriennummer eine korrekte Prüfziffer enthält:
        </h3>
        <p><b>Eingabe:</b> Zeichenkette der Seriennummer</p>
        <p><b>Ausgabe:</b>wahr oder falsch</p>
      </div>
      <div class="mb-3">
        <h3>Hinweis zum Zusammenhang von Seriennummer und Prüfziffer:</h3>
        <p>
          Die Seriennummer auf einem Geldschein besteht aus zwölf Zeichen. Die
          ersten beiden Zeichen sind Buchstaben und geben die Druckerei an, in
          der der Geldschein gedruckt wurde. Die folgenden neun Ziffern sind die
          eigentliche Seriennummer und die letzte Ziffer ist die Prüfziffer.
        </p>
        <p>
          Aus den ersten elf Zeichen lässt sich die Prüfziffer wie folgt
          errechnen:
        </p>
        <v-list-item v-for="checkdigit in checkdigits" :key="checkdigit.text">
          <v-list-item-content>
            <v-list-item-title v-text="checkdigit.text"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <p class="mt-3">
          Auf einem Geldschein ist z. B. die Seriennummer „SE7133131855"
          aufgedruckt. Somit ergibt sich:
        </p>
        <p>Kennzeichen der Druckerei: SE</p>
        <p>Seriennummer (9-stellig): 713313185</p>
        <p class="mb-3">Prüfziffer: 5</p>
      </div>
      <div class="mb-6">
        <h3>
          Für die Seriennummer „SE7133131855" ergibt sich folgende Rechnung:
        </h3>
        <v-list-item
          v-for="serialNumber in serialNumbers"
          :key="serialNumber.title"
        >
          <v-list-item-content>
            <v-list-item-title v-text="serialNumber.title"></v-list-item-title>
            <v-list-item-subtitle
              v-text="serialNumber.subtitle"
            ></v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <p>Die Prüfziffer stimmt mit der aufgedruckten Prüfziffer überein.</p>
      </div>
      <div class="text-center">
        <h3>Lösung</h3>
        <checkPruefziffer></checkPruefziffer>
      </div>
    </v-container>
  </div>
</template>

<script>
import checkPruefziffer from "@/components/checkPruefziffer";
export default {
  name: "sae1",
  components: {
    checkPruefziffer
  },
  data: () => ({
    checkdigits: [
      {
        text:
          "1. Die zwei Buchstaben werden durch die Zahl ihrer Reihenfolge im Alphabet ersetzt (also A=1, Z=26)."
      },
      {
        text:
          "2. Aus den zwei in Schritt 1 ermittelten Zahlen und der 9-stelligen Nummer wird eine Quersumme gebildet."
      },
      {
        text:
          "3. Die Quersumme wird durch 9 dividiert und der Rest aus dieser Division ermittelt."
      },
      {
        text:
          "4. Dieser Rest wird nun von 7 abgezogen, das Ergebnis ergibt die Prüfziffer."
      }
    ],
    serialNumbers: [
      {
        title: "1. Die beiden Buchstaben werden durch Zahlen ersetzt:",
        subtitle: "S=19 und E=5"
      },
      {
        title: "2. Die Quersumme wird aus der Zahl 195713313185 gebildet:",
        subtitle: "1+9+5+7+1+3+3+1+3+1+8+5=47"
      },
      { title: "3. 47/9", subtitle: "= 5 (Rest 2)" },
      { title: "4. 7-2", subtitle: "=5" }
    ]
  })
};
</script>

<style scoped></style>
