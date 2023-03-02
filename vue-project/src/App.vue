<template>
  <div class="app">
    <h2 class="header">Zadanie rekrutacyjne - Button</h2>
    <my-button color="primary" @click="isCollapsed = !isCollapsed">
      Nieaktywny przycisk
      <template #append> dodatkowa treść </template>
    </my-button>
    <pre class="code" v-show="!isCollapsed">
                <code >
                  {{ `
                    <template>
                      <v-btn v-bind="$attrs" v-on="$listeners">
                        <slot></slot>
                        <slot name="append"></slot>
                      </v-btn>
                    </template>

                  <script>
                                                                                                            export default {
                                                                                                            name: "MyButton",
                                                                                                            };
                                                                                                          </script>
                                                                                                          `
                  }}
                </code>
                </pre>
    <h2 class="header">Zadanie rekrutacyjne - Card</h2>
    <my-button color="primary" @click="isCollapsedCard = !isCollapsedCard">
      Pokaż kod
    </my-button>
    <pre class="code" v-show="!isCollapsedCard">
                      <code >
                        {{ `
                        countFullDecks(cards) {
                      let fullDecks = 0;

                      // Dawid aby ci było łatwiej, pokazuje i objaśniam co tu się dzieje

                      // sortujemy tablicę przez dane symbole pomoże to póznie przy filtrowaniu 

                      cards.sort(); // Dostajemy 0: 'AKAR', 1: 'AKIE', 2: 'APIK', 3: 'ATRE', 4: 'DKIE', 5: 'WKIE'}

                      // tworzymy tablicę z symbolami kart

                      const suits = ['W', 'D', 'K', 'A'];
                      const values = ['KAR', 'KIE', 'TRE', 'PIK'];

                      // tworzymy tablicę z kartami danego symbolu

                      const cardsOfSuit = cards.filter(card => {
                        for (let i = 0; i < suits.length; i++) return card.includes(suits[i])
                      }

                      );

                      // i tutaj moglibyśmy skończyć zadanie ale nie jestem juniorem i chciałem pokazać jak można to zrobić lepiej
                      // if(cardsOfSuit.length === 4) { 
                      //   fullDecks++;
                      // }


                                                                                                                                                      // Sprawdzanie czy tablica zawiera wszystkie wartości
                                                                                                                                                      if (cardsOfSuit.every((value) => values.includes(value.slice(1)))) {
                                                                                                                                                        fullDecks++;
                                                                                                                                                      }

                                                                                                                                                      return fullDecks;
                                                                                                                                                    }
                                                                                                                                                    `}}
                    </code>
                  </pre>
    <!-- Brak walidacji że względu n na brak czasu -->
    <v-text-field class="input" label="Napisz iniciał karty oraz zatwierdz enterem" type="text" v-model="newCard"
      @keyup.enter="addCard"></v-text-field>
    <h2>Liczba tali: {{ countFullDecks(cards) }}</h2>
    <Card v-for="item in cards.sort()" :key="item" :suit="item.slice(1)" :value="item.charAt(0)" />
  </div>
</template>

<script>
import MyButton from "./components/MyButton.vue";
import Card from "./components/Card.vue";

export default {
  name: "App",
  components: {
    MyButton,
    Card,
  },
  data() {
    return {
      isCollapsed: true,
      isCollapsedCard: true,
      cards: ['APIK', 'WKIE', 'AKIE', 'DKIE', 'ATRE', 'AKAR', 'DPIK', 'DTRE', 'DKAR'],
      newCard: '',
    };
  },
  methods: {
    addCard() {
      if (this.newCard) {
        this.cards.push(this.newCard);
        this.newCard = '';
      }
    },
    countFullDecks(cards) {
      let fullDecks = 0;
      const suits = ['W', 'D', 'K', 'A'];
      const values = ['KAR', 'KIE', 'TRE', 'PIK'];

      // Dawid aby ci było łatwiej, pokazuje i objaśniam co tu się dzieje

      // sortujemy tablicę przez dane symbole pomoże to póznie przy filtrowaniu 

      cards.sort(); // Dostajemy 0: 'AKAR', 1: 'AKIE', 2: 'APIK', 3: 'ATRE', 4: 'DKIE', 5: 'WKIE'}

      // tworzymy tablicę z symbolami kart


      // tworzymy tablicę z kartami danego symbolu

      for (let i = 0; i < suits.length; i++) {
        const cardsOfSuit = cards.filter(card =>
          card.includes(suits[i])
        )
        console.log(cardsOfSuit)
        // i tutaj moglibyśmy skończyć zadanie ale nie jestem juniorem i chciałem pokazać jak można to zrobić lepiej
        // if(cardsOfSuit.length === 4) { 
        //   fullDecks++;
        // }


        // Sprawdzanie czy tablica zawiera wszystkie wartości
        if (cardsOfSuit.every((value) => values.includes(value.slice(1)))) {
          fullDecks++;
        }

      }
      return fullDecks;
    }
  }
};
</script>

<style>
/* Global Styles */

body {
  min-height: 100vh;
  margin: 0;
  padding: 0;
  font-family: "Roboto", sans-serif;
  background-image: url("./components/bg.png");
  background-size: cover;
  color: #fff;
}

.app {
  margin: 0 auto;
  max-width: 600px;
  text-align: center;
  padding: 100px 0;
}

.code {
  text-align: left;
}

.header {
  margin: 20px 0;
}

.input {
  margin: 20px 0;
}
</style>
