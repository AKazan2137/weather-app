<template>
  <b-container class="bv-example-row" v-if="list">
    <b-row>
      <b-col>
        <b-list-group v-for="weath in list.data.list" :key="weath.dt_txt">
          <b-list-group-item button @click="selectedWeather=weath">
            <a>
              <span>{{weath.dt_txt}}</span>
            </a>
          </b-list-group-item>
        </b-list-group>
      </b-col>
      <b-col v-if="selectedWeather">
        <b-list-group>
          <b-list-group-item>
            <b-row class="my-1">
              <b-col sm="3">
                <label>temp:</label>
                <label>feels_like:</label>
                <label>temp_min:</label>
                <label>temp_max:</label>
              </b-col>
              <b-col sm="3">
                <b-form-input disabled v-model="selectedWeather.main.temp">temp</b-form-input>
                <b-form-input disabled v-model="selectedWeather.main.feels_like" />
                <b-form-input disabled v-model="selectedWeather.main.temp_min" />
                <b-form-input disabled v-model="selectedWeather.main.temp_max" />
              </b-col>
            </b-row>
          </b-list-group-item>
        </b-list-group>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import * as axios from "axios";
export default {
  name: "weather",
  props: {
    msg: String
  },
  data() {
    return {
      selectedWeather: undefined,
      showMore: false,
      list: []
    };
  },
  created() {},
  methods: {},
  mounted() {
    axios
      .get(
        "http://api.openweathermap.org/data/2.5/forecast?q=Warsaw&appid=9513741eb68c088a78d7e4fd5622e253&units=metric"
      )
      .then(response => (this.list = response));
  }
};
</script>

