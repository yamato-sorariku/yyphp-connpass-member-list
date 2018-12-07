<template>
  <section>
    <div 
      v-for=" event in events" 
      :key="event.id">
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
    const data = await this.$axios.$get('/events')
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
