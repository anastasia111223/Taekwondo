<template>
    <div class="projects pa-10">
        <v-row>
            <v-col cols="12">
                <h3>Список соревнований</h3>
            </v-col>
        </v-row>
        <div v-if="comps?.length">
            <div v-if="pastCompetitions?.length">
                <nuxt-link :to="`competition/${comp.id}`" class="text-decoration-none bluedeep--text d-flex align-end"></nuxt-link>
            </div>

        

        </div>
        <div>
            <nuxt-link :to="`newComp/`" class="text-decoration-none bluedeep--text d-flex align-end">
                <v-btn outlined color="#351BA9" rounded-xl
                    class="ma-1 d-block text-decoration-none font-weight-bold">
                    <v-icon left>
                    mdi-plus
                    </v-icon>Cоздать соревнование</v-btn>
            </nuxt-link>
        </div>

    </div>

</template>

<script>
export default {
  data () {
    return {
        comps: [],
        today: '',
    }
  },
  computed: {
    pastCompetitions() {
        if (comps?.length) return copms.filter(one => one.past)
        else return [];
    },
    futureCompetitions() {
        if (comps?.length) return copms.filter(one => !one.past)
        else return [];
    }
  },
  created() {
    this.today = new Date();
    this.today.setHour();
    this.today = this.today.getTime();

  },
}

</script>