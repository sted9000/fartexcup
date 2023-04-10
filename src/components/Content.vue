<template>
  <div class="content">

    <div class="intro">
<!--      subheader text-->
      <h1>2023 Lakeview Challenge</h1>
      <p>
        The Lakeview Challenge is a year long competition between the players of Lakeview Golf Club. Each player will compete against each other to see who can accumulate the most points over the season. Each unique birdie is worth one point and unique eagles are worth two. The player with the most points at the end of the season will be crowned the 2023 Lakeview Challenge Champion.</p>
    </div>

    <div class="leaderboard">
      <h2>Leaderboard</h2>
      <v-simple-table v-if="!mobileDisplay" :dense="true" :dark="false">
        <tbody>
        <tr>
          <th colspan="1"></th>
          <th style="text-align: center" colspan="9">Peak</th>
          <th style="text-align: center" colspan="9">Lake</th>
          <th style="text-align: center" colspan="9">Mountain</th>
          <th colspan="1">Points</th>
        </tr>
        <tr>
          <th colspan="1">Hole</th>
          <td v-for="hole in labels[0].holes" :key="hole"> {{ hole.name }} </td>
          <td v-for="hole in labels[1].holes" :key="hole"> {{ hole.name }} </td>
          <td v-for="hole in labels[2].holes" :key="hole"> {{ hole.name }} </td>
        </tr>
        <tr>
          <th colspan="1">Par</th>
          <td v-for="hole in labels[0].holes" :key="hole"> {{ hole.par }} </td>
          <td v-for="hole in labels[1].holes" :key="hole"> {{ hole.par }} </td>
          <td v-for="hole in labels[2].holes" :key="hole"> {{ hole.par }} </td>
        </tr>
        <tr>
          <th colspan="1">HCP</th>
          <td v-for="hole in labels[0].holes" :key="hole"> {{ hole.handicap }} </td>
          <td v-for="hole in labels[1].holes" :key="hole"> {{ hole.handicap }} </td>
          <td v-for="hole in labels[2].holes" :key="hole"> {{ hole.handicap }} </td>
        </tr>

        <tr v-for="player in players" :key="player">
          <th>{{player.name}}</th>
          <td >{{ player.p_1}}</td>
          <td >{{ player.p_2}}</td>
          <td >{{ player.p_3}}</td>
          <td >{{ player.p_4}}</td>
          <td >{{ player.p_5}}</td>
          <td >{{ player.p_6}}</td>
          <td >{{ player.p_7}}</td>
          <td >{{ player.p_8}}</td>
          <td >{{ player.p_9}}</td>
          <td >{{ player.l_1}}</td>
          <td >{{ player.l_2}}</td>
          <td >{{ player.l_3}}</td>
          <td >{{ player.l_4}}</td>
          <td >{{ player.l_5}}</td>
          <td >{{ player.l_6}}</td>
          <td >{{ player.l_7}}</td>
          <td >{{ player.l_8}}</td>
          <td >{{ player.l_9}}</td>
          <td >{{ player.m_1}}</td>
          <td >{{ player.m_2}}</td>
          <td >{{ player.m_3}}</td>
          <td >{{ player.m_4}}</td>
          <td >{{ player.m_5}}</td>
          <td >{{ player.m_6}}</td>
          <td >{{ player.m_7}}</td>
          <td >{{ player.m_8}}</td>
          <td >{{ player.m_9}}</td>
          <td>{{player.total}}</td>

        </tr>
        </tbody>
      </v-simple-table>
      <v-simple-table v-else :dense="true" :dark="false">
        <tbody>
        <tr>
          <th v-for="label in mobileLabels" :key="label"> {{ label }} </th>
        </tr>
        <tr v-for="player in players" :key="player">
          <td >{{ player.p_1}}</td>
          <td >{{ player.name}}</td>
          <td >{{ player.events}}</td>
          <td >{{ player.points}}</td>
        </tr>
        </tbody>
      </v-simple-table>
    </div>
  </div>

</template>

<script>
export default {
  name: "Content",
  props: {
    msg: String,
  },
  data() {
    return {
      labels: [
        { name: 'Peak', holes: [
            { name: '1', length: '376', par: '4', handicap: '4' },
            { name: '2', length: '323', par: '4', handicap: '7' },
            { name: '3', length: '348', par: '4', handicap: '5' },
            { name: '4', length: '163', par: '3', handicap: '8' },
            { name: '5', length: '438', par: '5', handicap: '3' },
            { name: '6', length: '372', par: '4', handicap: '6' },
            { name: '7', length: '396', par: '4', handicap: '1' },
            { name: '8', length: '155', par: '3', handicap: '9' },
            { name: '9', length: '545', par: '5', handicap: '2' },
          ]},
        { name: 'Lake', holes: [
            { name: '1', length: '405', par: '4', handicap: '2' },
            { name: '2', length: '465', par: '5', handicap: '5' },
            { name: '3', length: '321', par: '4', handicap: '4' },
            { name: '4', length: '157', par: '3', handicap: '8' },
            { name: '5', length: '480', par: '5', handicap: '7' },
            { name: '6', length: '350', par: '4', handicap: '3' },
            { name: '7', length: '314', par: '4', handicap: '6' },
            { name: '8', length: '160', par: '3', handicap: '9' },
            { name: '9', length: '382', par: '4', handicap: '1' },
          ]},
        { name: 'Mountain', holes: [
            { name: '1', length: '316', par: '4', handicap: '9' },
            { name: '2', length: '467', par: '4', handicap: '2' },
            { name: '3', length: '531', par: '5', handicap: '3' },
            { name: '4', length: '183', par: '3', handicap: '7' },
            { name: '5', length: '409', par: '4', handicap: '4' },
            { name: '6', length: '521', par: '5', handicap: '1' },
            { name: '7', length: '386', par: '4', handicap: '5' },
            { name: '8', length: '157', par: '3', handicap: '8' },
            { name: '9', length: '331', par: '4', handicap: '6' },
          ]},

      ],
      mobileLabels: [
        "Rank",
        "Name",
        "Events",
        "Points",
      ],
      players: [
        {
          name: "J. Shank",
          p_1: "0",
          p_2: "0",
          p_3: "0",
          p_4: "0",
          p_5: "0",
          p_6: "0",
          p_7: "0",
          p_8: "0",
          p_9: "0",
          l_1: "0",
          l_2: "0",
          l_3: "0",
          l_4: "0",
          l_5: "0",
          l_6: "0",
          l_7: "1",
          l_8: "0",
          l_9: "0",
          m_1: "0",
          m_2: "0",
          m_3: "0",
          m_4: "0",
          m_5: "0",
          m_6: "0",
          m_7: "1",
          m_8: "0",
          m_9: "0",
          total: "2"
        },
        {
          name: "J. Krech",
          p_1: "0",
          p_2: "0",
          p_3: "0",
          p_4: "0",
          p_5: "0",
          p_6: "0",
          p_7: "0",
          p_8: "0",
          p_9: "0",
          l_1: "0",
          l_2: "1",
          l_3: "0",
          l_4: "0",
          l_5: "1",
          l_6: "0",
          l_7: "0",
          l_8: "0",
          l_9: "0",
          m_1: "0",
          m_2: "0",
          m_3: "0",
          m_4: "0",
          m_5: "1",
          m_6: "0",
          m_7: "0",
          m_8: "0",
          m_9: "0",
          total: "3"
        },
        {
          name: "T. Slocum",
          p_1: "0",
          p_2: "0",
          p_3: "0",
          p_4: "1",
          p_5: "0",
          p_6: "0",
          p_7: "0",
          p_8: "0",
          p_9: "1",
          l_1: "0",
          l_2: "0",
          l_3: "0",
          l_4: "0",
          l_5: "1",
          l_6: "0",
          l_7: "0",
          l_8: "0",
          l_9: "0",
          m_1: "0",
          m_2: "0",
          m_3: "1",
          m_4: "0",
          m_5: "0",
          m_6: "1",
          m_7: "0",
          m_8: "1",
          m_9: "0",
          total: "6"
        },

      ],
    };
  },
  computed: {
    mobileDisplay() {
      return this.$vuetify.breakpoint.smAndDown;
    },
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.content {
  text-align: center;
}

.intro {
  margin: 0 auto;
  width: 90%;
  max-width: 800px;
}

.leaderboard {
  margin: 50px auto;
  max-width: 1400px;
}


</style>
