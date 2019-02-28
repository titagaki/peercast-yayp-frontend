<template>
  <div class="channel-list">
    <vs-table search max-items="3" pagination :data="channels">
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
        <vs-tr :key="indextr" v-for="(tr, indextr) in data" >
          <vs-td :data="data[indextr].Name">
            <p>{{data[indextr].Name}}</p>
            <p>[{{data[indextr].Genre}} - {{data[indextr].Description}}]「{{data[indextr].Comment}}」</p>
          </vs-td>

          <vs-td :data="data[indextr].Listeners">
            <p>{{data[indextr].Listeners}} / {{data[indextr].Relays}}</p>
            <p>{{data[indextr].Age}}</p>
          </vs-td>

          <vs-td :data="data[indextr].ContentType">
            <p>{{data[indextr].ContentType}}</p>
            <p>{{data[indextr].Bitrate}} kbps</p>
          </vs-td>
        </vs-tr>
      </template>
    </vs-table>
  </div>
</template>

<script>
  export default {
    data:()=>({
      channels:[{"ID":8,"GnuID":"1FAF45207E3CF1CB28838893A71B224B","Name":"kkt","Bitrate":1660,"ContentType":"FLV","Listeners":8,"Relays":5,"Age":70,"Genre":"game","Description":"Project Zomboid","Url":"http://jbbs.shitaraba.net/bbs/read.cgi/game/60476/1549254358/","Comment":"死ぬマン にんげんとのたたかい","TrackArtist":"","TrackTitle":"","TrackAlbum":"","TrackGenre":"","TrackContact":"","HiddenListeners":false,"TrackerIP":"121.115.0.152:7144","TrackerDirect":false,"IsPlaying":true},{"ID":9,"GnuID":"C19506B7717D474F7884E999638DE3DF","Name":"だいちゃ","Bitrate":1628,"ContentType":"FLV","Listeners":7,"Relays":5,"Age":205,"Genre":"Game","Description":"テトリス99","Url":"http://jbbs.shitaraba.net/bbs/read.cgi/game/37056/1531041366/","Comment":"まったり短時間","TrackArtist":"","TrackTitle":"","TrackAlbum":"","TrackGenre":"","TrackContact":"","HiddenListeners":false,"TrackerIP":"133.232.141.34:7155","TrackerDirect":false,"IsPlaying":true},{"ID":10,"GnuID":"D80DE8FA12561E649E95A6DE3BAE9C63","Name":"0501","Bitrate":1914,"ContentType":"FLV","Listeners":5,"Relays":14,"Age":216,"Genre":"","Description":"なんもしません","Url":"http://jbbs.shitaraba.net/music/29690/","Comment":"","TrackArtist":"","TrackTitle":"","TrackAlbum":"","TrackGenre":"","TrackContact":"","HiddenListeners":false,"TrackerIP":"210.255.248.80:7144","TrackerDirect":false,"IsPlaying":true},{"ID":11,"GnuID":"904EAAA0968D40F787C350EA7A7C4276","Name":"ひゅっくり","Bitrate":1628,"ContentType":"FLV","Listeners":12,"Relays":13,"Age":220,"Genre":"Game","Description":"Euro Truck Simulator 2","Url":"http://hyuku.net/test/read.cgi/bbs/1550257345/","Comment":"無免許なのに5拠点目開設を目指す！","TrackArtist":"","TrackTitle":"","TrackAlbum":"","TrackGenre":"","TrackContact":"","HiddenListeners":false,"TrackerIP":"60.112.35.218:7144","TrackerDirect":false,"IsPlaying":true}]
    }),
  }
</script>

<style lang="stylus" scoped>
  .channel-list
    width 70%
    margin: auto
  td
    text-align left
</style>