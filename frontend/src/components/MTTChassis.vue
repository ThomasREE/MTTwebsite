<template>
  <div class="MTTChassis">
    <h1>{{ msg1 }}</h1>
    <h1>{{ msg2 }}</h1>
    <hr />
    <img
      alt="FENETRES PLIANTES PISCINE"
      src="../assets/FENETRES PLIANTES PISCINE.jpg"
      img
      width="40%"
    />
    &nbsp;&nbsp;
    <!--label-->
    <input type="checkbox" name="chassis1" value="valeur" v-model="chassis1" />
    Je suis intéressé par ce produit
    <!--/label-->
    <!--pre></pre-->
    <hr />
    <img
      alt="FENETRE PISCINE 2"
      src="../assets/FENETRE PISCINE 2.jpg"
      img
      width="40%"
    />
    &nbsp;&nbsp;
    <input type="checkbox" name="chassis2" value="valeur" v-model="chassis2" />
    Je suis intéressé par ce produit
    <hr />
    <img
      alt="FENETRES CORSE"
      src="../assets/FENETRES CORSE.jpg"
      img
      width="40%"
    />
    &nbsp;&nbsp;
    <input type="checkbox" name="chassis3" value="valeur" v-model="chassis3" />
    Je suis intéressé par ce produit
    <hr />
    <img
      alt="FENETRES PLIANTES 5VTX"
      src="../assets/FENETRES PLIANTES 5VTX.jpg"
      img
      width="40%"
    />
    &nbsp;&nbsp;
    <input type="checkbox" name="chassis4" value="valeur" v-model="chassis4" />
    Je suis intéressé par ce produit
    <hr />
    <img
      alt="FENETRES PLIANTES 6VTX"
      src="../assets/FENETRES PLIANTES 6VTX.jpg"
      img
      width="40%"
    />
    &nbsp;&nbsp;
    <input type="checkbox" name="chassis5" value="valeur" v-model="chassis5" />
    Je suis intéressé par ce produit
    <hr />
    <img alt="PLIANTES 2" src="../assets/PLIANTES 2.jpg" img width="66%" />
    &nbsp;&nbsp;
    <input type="checkbox" name="chassis6" value="valeur" v-model="chassis6" />
    Je suis intéressé par ce produit
    <hr />
    <video
      ref="videoFenetresAccordeon"
      src="../assets/Fenetres Accordéon Méditerranée Techniques Travaux.webm"
      width="1000"
    ></video>
    <!--hr    hr prints a line and makes a carriage return, whereas pre does a simple carriage return-->
    <button class="button btn-primary" v-on:click="playStop">
      Jouer / Arrêter
    </button>
    <!--button :disabled="isPlaying" @click="play">Jouer</button>
    <button :disabled="!isPlaying" @click="stop">Arrêter</button-->
    &nbsp;&nbsp;
    <input type="checkbox" name="chassis7" value="valeur" v-model="chassis7" />
    Je suis intéressé par ce produit
    <hr />
    <b>
      Nom{{ espace }}{{ espace }}{{ espace }}{{ espace }}{{ espace }}{{ espace
      }}{{ espace }}{{ espace }}{{ espace }}{{ espace }}{{ espace
      }}{{ espace }} <input v-model="nom" />
      <pre></pre>
      Prénom{{ espace }}{{ espace }}{{ espace }}{{ espace }}{{ espace
      }}{{ espace }} <input v-model="prenom" />
      <pre></pre>
      Téléphone{{ espace }}{{ espace }} <input v-model="telephone" />
      <pre></pre>
      E-mail{{ espace }}{{ espace }}{{ espace }}{{ espace }}{{ espace
      }}{{ espace }}{{ espace }}{{ espace }}{{ espace }}
      <input v-model="mail" />
      <pre></pre>
    </b>
    <h1>
      {{ espace }}{{ espace }}{{ espace }}{{ espace }}{{ espace }} {{ espace
      }}{{ espace }}{{ espace }}{{ espace }}{{ espace }}
      <button class="button btn-primary" v-on:click="postMTTchassis">
        INFORMER MTT
      </button>
    </h1>
    <pre></pre>
    <pre></pre>
  </div>
</template>

<script>
import axios from "axios";
//import Vue from 'vue'
// import VeeValidate from 'vee-validate'
/* eslint-disable */
//Vue.use(VeeValidate)
export default {
  name: "MTTChassis",

  data: function () {
    return {
      produits: [8],
      isPlaying: false,
      chassis1: false, // TO DO : of course array of bool to regroup all my choices
      chassis2: false, // TO DO : of course array of bool to regroup all my choices
      chassis3: false, // TO DO : of course array of bool to regroup all my choices
      chassis4: false, // TO DO : of course array of bool to regroup all my choices
      chassis5: false, // TO DO : of course array of bool to regroup all my choices
      chassis6: false, // TO DO : of course array of bool to regroup all my choices
      chassis7: false, // TO DO : of course array of bool to regroup all my choices
      nom: "",
      prenom: "",
      telephone: "",
      mail: "",
      espace: "\xa0",
    };
  },

  props: {
    msg1: String,
    msg2: String,
  },

  methods: {
    playStop() {
      if (this.isPlaying) this.$refs.videoFenetresAccordeon.pause();
      else this.$refs.videoFenetresAccordeon.play();
      this.isPlaying = !this.isPlaying;
    },
    postMTTchassis: function () {
      var dataFromMTT = {
        nom: this.nom,
        prenom: this.prenom,
        telephone: this.telephone,
        mail: this.mail,
      };

      console.log(dataFromMTT);

      axios({
        method: "POST",
        url: "http://127.0.0.1:8090/mttChassis",
        data: dataFromMTT,
        headers: { "content-type": "text/plain" },
      })
        .then((result) => {
          console.log(result.data);
          alert(result.data["messageServer"])
        })
        .catch((error) => {
          console.error(error);
          alert("Serveur MTT indisponible")
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
</style>