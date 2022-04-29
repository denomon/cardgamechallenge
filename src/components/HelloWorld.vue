<template>
  <div class="hello" id="home">
    <h1>{{ msg }}</h1>
    <hr/>

    <h3>SCORE: {{ PlayerCardScoreValues.length }} </h3>
    <h2>Is the next card Greater than the card dispalyed?</h2>
    {{ playerMessage }}
    <button v-if="playerLostGame || PlayerCardScoreValues.length == toWinScore " type="button" value="Reload Page" onclick="window.location.reload()"> Restart</button>

    <!-- Calling function in methods -->
    <div  class="select-buttons">
      <div v-if="!playerLostGame" class="buttons">
        <button @click="no">No!</button>
        <button @click="yes">Yes!</button>
      </div>
    </div>

    <div id="stillPlaying">
      <div class="card center">
        <span class="card-value-suit top">{{ this.cardStack[0] }}</span>
        <span class="card-value-suit bot">{{ this.cardStack[0] }}</span>
      </div>
    </div>
  </div>

</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  el: "#home",
  data() {
    return {
      cardValues: ["2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K", "A"],
      counter: 0,
      playerChoice: true,
      playerLostGame: false,
      toWinScore: 5,
      currentCardValue: 0,
      cardStack: [],
      nextCardValue: 0,
      playerMessage: 'Click below to find out!',
      PlayerCardScoreValues: []
    };
  },
  methods: {
    // Creating function

    createStack: function () {
      for (var decknumber = 0; decknumber <= 51; decknumber++) {
        var chosenNumber = Math.floor(Math.random() * this.cardValues.length);
        this.cardStack[decknumber] = this.cardValues[chosenNumber];
      }
    },
    show: function () {
      //Create the stack
      this.createStack();
      this.currentCardValue = this.cardStack[0];
    },
    yes: function () {
      this.playerChoiceSelected('YES');
    },
    no: function () {
      this.playerChoiceSelected('NO');
    },
    playerChoiceSelected: function (playerChoice) {
      this.counter++;

      //check if the next card value is highyer than current
      this.nextCardValue = this.cardStack[this.counter];

      //Check if they have scored or not
      if (
          (playerChoice == "YES" && this.cardValues.indexOf(this.nextCardValue) > this.cardValues.indexOf(this.currentCardValue)) ||
          (playerChoice == "NO" && this.cardValues.indexOf(this.nextCardValue) < this.cardValues.indexOf(this.currentCardValue))
      ) {
        this.PlayerCardScoreValues.push(this.currentCardValue);
        this.playerMessage = (this.PlayerCardScoreValues.length === this.toWinScore) ? 'You have WON the Game' : 'Good Choice! Have another go.';

      } else if (this.cardValues.indexOf(this.nextCardValue) == this.cardValues.indexOf(this.currentCardValue)) {
        this.playerLostGame = true;
        this.playerMessage = 'You have lost the GAME!';
        this.PlayerCardScoreValues.length = 0;
      } else {
        this.playerLostGame = true;
        this.playerMessage = 'You have lost the GAME!';
        this.PlayerCardScoreValues.length = 0;
      }
      this.appendWinnerCards(this.nextCardValue, "stillPlaying");
      this.currentCardValue = this.nextCardValue;
    },
    appendWinnerCards: function (scoredCardValue, id) {
      const card = document.createElement("div");
      card.classList.add("card");
      card.classList.add("center");
      card.innerHTML =
          '<span class="card-value-suit top">' + scoredCardValue + '</span>' +
          '<span class="card-value-suit top">' + scoredCardValue + '</span>' +
          '<span class="card-value-suit bot">' + scoredCardValue + '</span>';
      document.getElementById(id).appendChild(card);
    }

  },
  beforeMount() {
    this.show()
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

hr {
  border: 0;
  border-top: 2px solid brown;
}

.center {
  margin: 0 auto;
  text-align: center;
}

.select-buttons {
  margin: 40px;

}

.buttons {
  margin: 40px;

}
</style>
