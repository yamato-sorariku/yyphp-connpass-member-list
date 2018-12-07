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
export default {
  transition: 'slide-left',
  data: () => ({
    activeLoading: true,
    event: {},
    frames: []
  }),
  mounted: async function() {
    this.$vs.loading()
    const data = await this.$axios.$get('/events/' + this.$route.query.id)
    this.event = data.event
    this.frames = data.frames
    this.$vs.loading.close()
  }
}
</script>

<style>
</style>
