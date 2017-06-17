<template>
    <div>
      <div class="hero tac">
        <h1>Get halp!</h1>
        <h3>What do you need halp with</h4>
        <br>

        <select id="skill">
          <option value="babysitting">Babysitting</option>
          <option value="Lawn Mowing">Lawn Mowing</option>
          <option value="snow-blowing">Snow Blowing</option>
        </select>
        <br>
        <p> </p>
        <!--<p> </p>-->
        <div id="help-button">
          <a class="btn  btn--light hint--bottom  big-create-btn" aria-label="Get some halp!" @click="getHelp">Find Halp!</a>
        </div>
        <table id="results">
        </table>
      </div>
    </div>
</template>

<script>
import { auth } from '../Auth.js';
import itemService from '../ItemService.js';
import ItemTile from '../ItemTile.vue';

export default {
  components: { ItemTile },

  data () {
    return {
      name: 'Home',
      popularItems: [],
      recentItems: []
    }
  },

  ready () {
      var skills = firebase.database().ref('skills').orderByKey();
    //   console.log(skills);
      skills.once('value').then(function(snapshot) {
          var skillData = snapshot.val();
          var numSkills = Object.keys(skillData).length;
          var skillList = Object.keys(skillData);
          console.log(skillList);
        // var users = snapshot.val()
        // var numUsers = Object.keys(users).length;
        // var keys = Object.keys(users);
        for (var i = 0; i < numSkills; i++) {
          console.log(skillList[i]);
        } 
      });
  },

  created() {
    var self = this;
  },

  methods: {
    onCreateClick() {
      if (auth.isLoggedIn) {
        this.$route.router.go({ name: 'new' });
      } else {
        this.$dispatch('openLoginDialogEvent')
      }
    },
    addSkill() {
      console.log('TODO add skill');
    },
    getHelp() {
      var e = document.getElementById("skill");
      var skill = e.options[e.selectedIndex].value;
      var table = document.getElementById("results");

      console.log(skill);

      var usersRef = firebase.database().ref('users');
      usersRef.once('value').then(function(snapshot) {
        var users = snapshot.val()
        var numUsers = Object.keys(users).length;
        var keys = Object.keys(users);
        for (var i = 0; i < numUsers; i++) {
          if ("skills" in users[keys[i]])
            if (skill in users[keys[i]]["skills"]) {
              console.log(users[keys[i]])
              var row = document.createElement("tr");
              var cell = document.createElement("td");    
              var cellText = document.createTextNode(users[keys[i]]["displayName"]);
              cell.appendChild(cellText);
              row.appendChild(cell);
              table.appendChild(row);
            }
        } 
      });
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
