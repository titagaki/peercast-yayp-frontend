<template>
  <div class="ch-list">
    <vs-table
            search
            pagination
            max-items="3"
            :data="channels">
      <template slot="header">
        <h3>
          現在配信中のチャンネル
        </h3>
      </template>
      <template slot="thead">
        <vs-th>
          Channel
        </vs-th>
        <vs-th>
          Status
        </vs-th>
        <vs-th>
          Type
        </vs-th>
      </template>

      <template slot-scope="{data}">
        <vs-tr :data="tr" :key="i" v-for="(tr, i) in data">
          <vs-td>
            {{ data[i].Name }}<br>
            [{{ data[i].Genre }} - {{ data[i].Description }}]「{{ data[i].Comment }}」
          </vs-td>

          <vs-td>
            {{ data[i].Listeners }} / {{ data[i].Relays }}<br>
            {{ formatTime(data[i].Age) }}
          </vs-td>

          <vs-td>
            {{ data[i].ContentType }}<br>
            {{ data[i].Bitrate }} kbps
          </vs-td>
        </vs-tr>
      </template>
    </vs-table>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        channels: []
      }
    },
    mounted() {
      const url = '/api/channels';
      fetch(url)
        .then(response => {
          if (!response.ok) {
            return;
          }
          response.json().then(json => {
            this.channels = json
          });
        })
    },
    methods: {
      formatTime(t) {
        const s = t % 60;
        t = (t - s) / 60;
        const m = t % 60;
        const h = (t - m) / 60;
        return h + ':' + (m < 10 ? '0' + m : m);
      }
    }
  }
</script>

<style lang="stylus" scoped>
  .ch-list
    width: 70%
    margin: auto
  td
    text-align: left
</style>