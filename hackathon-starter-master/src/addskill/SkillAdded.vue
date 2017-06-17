<template>
    <div>
      <div class="hero tac">
        <h1>You have added a skill!</h1>
        <h3>What do you want to do now?</h4>
        <br>
        <br>
        <p> </p>
        <!--<p> </p>-->
        <div>
          <a class="btn  btn--light hint--bottom  big-create-btn" aria-label="Get halp!" @click="gethelpClick">Get Halp!</a>
          <a class="btn  btn--light hint--bottom  big-create-btn" aria-label="Add another skill!" @click="addskillClick">Halp Someone!</a>
        </div>
      </div>
    </div>
</template>

<script>
import { auth } from '../Auth.js';
import itemService from '../ItemService.js';
import ItemTile from '../ItemTile.vue';

export default {
  // components: { ItemTile },

  data: function() {
    return {
      skill: '',
      // userId: 'm7v9zLbVzXYAFeK1bXOl42ryhL92'
    }
  },

  route: {
    data: function (transition) {
      var self = this;
      // var userId = firebase.auth().currentUser.uid;
      // userId = 'm7v9zLbVzXYAFeK1bXOl42ryhL92';

      // firebase.database().ref('/users/' + userId + '/skills').set({
      //   skills: [skill]
      // });
    }
  },

  created() {
    var self = this;
  },

  methods: {
    addskillClick() {
      if (auth.isLoggedIn) {
        this.$route.router.go({ name: 'addskill' });
      } else {
        this.$dispatch('openLoginDialogEvent')
      }
    },
    gethelpClick() {
      if (auth.isLoggedIn) {
        this.$route.router.go({ name: 'search' });
      } else {
        this.$dispatch('openLoginDialogEvent')
      }
    },
    addSkill(data) {
      var skill = document.getElementById('skill').value;
      // var skill = data.skill
      var userId = firebase.auth().currentUser.uid;
      firebase.database().ref('/users/' + userId + '/skills/' + skill).set('True');
      firebase.database().ref('/skills/' + skill).set('True');
    }
  }
}
</script>

<style scoped>
  h1 {
    font-size: 4.5em;
    margin-bottom: 10px;
  }
  h3 {
    margin-top: 10px;
    opacity: 0.7;
    letter-spacing: 2px;
  }
  .hero {
    height: calc(100vh - 50px);
    display: flex;
    align-items: center;
    flex-direction: column;
    justify-content: center;
    /*background: radial-gradient(rgba(0,0,0,0.10) 15%, transparent 16%) 0 0, radial-gradient(rgba(0,0,0,0.1) 15%, transparent 16%) 8px 8px, radial-gradient(rgba(255,255,255,.1) 15%, transparent 20%) 0 1px, radial-gradient(rgba(255,255,255,.1) 15%, transparent 20%) 8px 9px;*/
    background-size: 16px 16px;
    /*background-color: var(--brand-color); #6543a9;*/
    background-color: #E08E79;
    color: white;
  }
  .big-create-btn {
    font-size: 2em;
  }
  @media screen and (max-width: 600px) {
    .hero__logo {
      display: none;
    }
  }
</style>
