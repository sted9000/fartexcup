<template>
  <div class="content">

    <div class="intro">
      <p>
        The FartExCup, sponsored by (you guessed it!) FartEx, is home to some of
        the most mediocre golfers in Philadelphia and is hosted on only the most
        convenient courses around. In our ongoing efforts to promote equity,
        diversity, and inclusion at FartEx, all golfers must be male and Jewish
        (or can pass as a Jew). The prizes are modest but the glory is eternal.
      </p>
    </div>

    <div class="leaderboard">
      <h1>Leaderboard</h1>
      <v-simple-table :dense="true" :dark="false">
        <tbody>
        <tr>
          <th v-for="label in labels" :key="label"> {{ label }} </th>
        </tr>
        <tr v-for="player in players" :key="player">
          <td >{{ player.twRank}}</td>
          <td >{{ player.lwRank}}</td>
          <td >{{ player.name}}</td>
          <td >{{ player.events}}</td>
          <td >{{ player.points}}</td>
          <td >{{ player.wins}}</td>
          <td >{{ player.ctPin}}</td>
          <td >{{ player.lDrives}}</td>
          <td >{{ player.pointBehind}}</td>
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
        "This Week's Rank",
        "Last Week's Rank",
        "Player's Name",
        "Events Played",
        "Points",
        "Wins",
        "Closest to Pin",
        "Longest Drive",
        "Points Behind",
      ],
      players: [
        {
          twRank: "1",
          lwRank: "3",
          name: "Josh",
          events: "3",
          points: "45",
          wins: "1",
          ctPin: "3",
          lDrives: "2",
          pointBehind: "-",
        },
        {
          twRank: "1",
          lwRank: "3",
          name: "Ted",
          events: "3",
          points: "45",
          wins: "1",
          ctPin: "3",
          lDrives: "2",
          pointBehind: "10",
        },
        {
          twRank: "1",
          lwRank: "3",
          name: "Ryan",
          events: "3",
          points: "45",
          wins: "1",
          ctPin: "3",
          lDrives: "2",
          pointBehind: "20",
        },
        {
          twRank: "1",
          lwRank: "3",
          name: "Rico",
          events: "3",
          points: "45",
          wins: "1",
          ctPin: "3",
          lDrives: "2",
          pointBehind: "22",
        },
      ],
    };
  },
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
  max-width: 1000px;
}



</style>
