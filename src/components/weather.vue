<template>
  <b-container class="bv-example-row">
    <b-row>
      <b-col>
        <b-list-group v-for="weath in weather" :key="weath.id">
          <b-list-group-item button @click="selectedWeather=weath">
            <a>
              <span>{{weath.id}}</span>
            </a>
          </b-list-group-item>
        </b-list-group>
      </b-col>
      <b-col>
        <b-list-group>
          <b-list-group-item disabled>
            <a>
              <input v-model="selectedWeather.id" />
              <input v-model="selectedWeather.country" />
              <input v-model="selectedWeather.city" />
              <input v-model="selectedWeather.tempToday" />
            </a>
          </b-list-group-item>
        </b-list-group>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  name: "weather",
  props: {
    msg: String
  },
  data() {
    return {
      selectedWeather: {
        id: 1,
        country: "",
        city: "",
        tempToday: 0
      },
      weather: [
        {
          id: 1,
          country: "Poland",
          city: "Warsaw",
          tempToday: 20.5
        },
        {
          id: 2,
          country: "Poland",
          city: "Cracow",
          tempToday: 22
        },
        {
          id: 3,
          country: "Poland",
          city: "Gdynia",
          tempToday: 23
        }
      ]
    };
  }
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
