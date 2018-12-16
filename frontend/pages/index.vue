<template>
  <section>
    <vs-row vs-justify="center">
      <vs-col 
        type="flex" 
        vs-justify="center" 
        vs-align="center" 
        vs-lg="8"
        vs-sm="12">
        <vs-divider 
          border-style="solid">
          開催予定のYYPHP一覧
        </vs-divider>
      </vs-col>
    </vs-row>
    <div 
      v-for=" event in events" 
      :key="event.id">
      <vs-row vs-justify="center">
        <vs-col 
          type="flex" 
          vs-justify="center" 
          vs-align="center" 
          vs-lg="8"
          vs-sm="12">
          <vs-card>
            <div slot="header">
              <h3>
                {{ event.title }}
              </h3>
            </div>
            <div>
              <div>
                <span>開催日時</span>
                <span>{{ event.event_date }}</span>
              </div>
              <div>
                <span>参加者人数</span>
                <span>{{ event.participants }} 人</span>
              </div>
            </div>
            <div slot="footer">
              <vs-row vs-justify="flex-end">
                <vs-button 
                  :href="event.event_page_url"
                  type="gradient" 
                  color="success" 
                  icon="link"
                  target >
                  CONNPASS
                </vs-button>
                <vs-button 
                  type="gradient" 
                  color="success" 
                  icon="description"
                  @click="clickDetail(event)">
                  詳細情報
                </vs-button>
              </vs-row>
            </div>
          </vs-card>
        </vs-col>
      </vs-row>
      <vs-row vs-justify="center">
        <vs-col 
          type="flex" 
          vs-justify="center" 
          vs-align="center" 
          vs-lg="8"
          vs-sm="12">
          <vs-divider 
            border-style="solid" />
        </vs-col>
      </vs-row>
      <vs-row vs-justify="center">
        <vs-col 
          type="flex" 
          vs-justify="center" 
          vs-align="center" 
          vs-lg="8"
          vs-sm="12">
          <vs-card class="cardx">
            <div slot="header">
              <h3>
                YYPHPとは?
              </h3>
            </div>
            <div>
              <p>
                YYPHPは一言で「PHPerの部室」です。PHPについて、雑に、ゆるく、ワイワイ話し合う集いです。毎回お題を決めずに雑談を出発点にいろいろなことを突発的にやります。集まった人でコードリーディングをすることもあれば、一緒に開発ツールを触ってみたり、フレームワークについての情報交換をすることもあります。開催は毎週高田馬場19:00にて。
              </p>
              <cite>
                <a href="https://yyphp.connpass.com/">YYPHP connpassグループの説明</a>より引用
              </cite>
            </div>
          </vs-card>
        </vs-col>
      </vs-row>
      <vs-row vs-justify="center">
        <vs-col 
          type="flex" 
          vs-justify="center" 
          vs-align="center" 
          vs-lg="8"
          vs-sm="12">
          <vs-divider 
            border-style="solid" />
        </vs-col>
      </vs-row>
      <vs-row vs-justify="center">
        <vs-col 
          type="flex" 
          vs-justify="center" 
          vs-align="center" 
          vs-lg="8"
          vs-sm="12">
          <vs-card class="cardx">
            <div slot="header">
              <h3>
                本サイトについて
              </h3>
            </div>
            <div>
              <p>
                本サイトは<a href="https://twitter.com/yamato_ja1461">@yamato_ja1461</a>が「YYPHP アドベントカレンダー」の記事に使うために作成したものです。
              </p>
              <p>
                本サイトの情報は１時間おきに実行されるバッチ処理によりconnpassから取得しています。
                そのため、最新の情報が表示されているというわけではありませんでのご注意ください。
              </p>
            </div>
          </vs-card>
        </vs-col>
      </vs-row>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  },
  data: () => ({
    activeLoading: true,
    events: []
  }),
  mounted: async function() {
    this.$vs.loading()
    const data = await this.$axios.$get('/api/events')
    this.events = data.events
    this.$vs.loading.close()
  },
  methods: {
    clickDetail: function(event) {
      this.$router.push('detail?id=' + event.id)
    }
  }
}
</script>

<style>
</style>
