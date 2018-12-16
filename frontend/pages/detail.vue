<template>
  <section>
    <vs-row vs-justify="center">
      <vs-col 
        type="flex" 
        vs-justify="center" 
        vs-align="center" 
        vs-lg="8"
        vs-w="12">
        <vs-card>
          <div slot="header">
            <h3>
              {{ event.title }}
            </h3>
          </div>
          <div>
            開催日： {{ event.event_date }}<br>
            参加者人数：{{ event.participants }} 人
          </div>
          <div slot="footer">
            <vs-row vs-justify="flex-end">
              <vs-button 
                :class="'clipcopy'" 
                :data-clipboard-text="createTextForHackMD()"
                type="gradient"
                color="success" 
                icon="description">
                クリップボードにコピー
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
        vs-w="12">
        <vs-list>
          <div 
            v-for="(frame, frameIndex) in frames" 
            :key="'frame_' + frameIndex">
            <vs-list-header 
              :title="frame.name" />
            <div 
              v-for="(member, memberIndex) in frame.members" 
              :key="'member_' + frameIndex + '_' + memberIndex">
              <vs-list-item 
                :title="member.name">
                <template slot="avatar">
                  <vs-avatar :src="member.icon_url"/>
                </template>
              </vs-list-item>
            </div>
          </div>
        </vs-list>
      </vs-col>
    </vs-row>
  </section>
</template>

<script>
import clipboard from 'clipboard'

export default {
  transition: 'slide-left',
  data: () => ({
    activeLoading: true,
    event: {},
    frames: [],
    clipBoard: {}
  }),
  mounted: async function() {
    let vm = this
    //setup for clipboard
    this.clipBoard = new clipboard('.clipcopy')
    this.clipBoard.on('success', function(e) {
      e.clearSelection()

      vm.$vs.notify({
        title: 'copied',
        text: 'copied for HackMD.'
      })
    })
    this.clipBoard.on('error', function(e) {})

    this.$vs.loading()
    const data = await this.$axios.$get('/api/events/' + this.$route.query.id)
    this.event = data.event
    this.frames = data.frames
    this.$vs.loading.close()
  },
  methods: {
    createTextForHackMD: function() {
      let mdText = this.event.title + '\n\n'

      mdText =
        mdText +
        '①PHP歴、②話したいこと/聞きたいこと、③簡単な自己紹介（オプション）'

      for (let frame of this.frames) {
        mdText = mdText + '\n\n## ' + frame.name + '\n'
        for (let member of frame.members) {
          mdText = mdText + '* ' + member.name + '\n'
        }
      }

      return mdText
    }
  }
}
</script>

<style>
#for-hackmd-text {
  display: none;
}
</style>
