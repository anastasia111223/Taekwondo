<template>
    <div class="projects pa-10">
        <v-row>
            <v-col cols="12">
                <h3>Создание нового соревнования</h3>
            </v-col>
        </v-row>
        <div>
        </div>

    </div>

</template>

<script>
export default {
  data () {
    return {
        comp: {
            name: '',
            date: '',
            city:'',
        },
        competitors: [],
        judges: [],
        today: '',
    }
  },
  computed: {
  },
  created() {
    // let comp = this.$store.getters.competitions.find(a => a.id_project.toString() === this.$route.params.id)

  },
}

</script>