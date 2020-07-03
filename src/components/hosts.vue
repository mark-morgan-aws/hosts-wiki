// hosts.vue

<template>
  <div>
    <h1>Hosts</h1>
    <button v-on:click="getHostsData">Get Host Data</button>
    <div v-for="hostData in hostsDataList" :key="hostData.id" class="hosts-data">
      <div class="host">
        <div>
          <span>{{hostData.hostname}}</span>
        </div>
        <div>
          <span class="domain">[[{{hostData.domain}}]]</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: "Hosts",
  data() {
    return {
      hostsDataList: []
    };
  },
  methods: {
    getHostsData() {
      //fetch("hosts.json")
      //  .then(response => response.json())
      //  .then(data => (this.hostsDataList = data));

        axios.get("hosts.json").then(response => (this.hostsDataList = response.data));
    }
  }
};
</script>