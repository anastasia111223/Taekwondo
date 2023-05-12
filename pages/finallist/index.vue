<template>
    <div class="projects pa-10">
        <v-row>
            <v-col cols="12">
                <h1>Результаты соревнований</h1>
            </v-col>
        </v-row>
        <div v-for="(com, i) in comp" :key="i">
            <!-- <v-list v-if="comp?.length">
                <v-list-group v-for="(com, i) in comp" :key="i"
                    variant="plain">
                    <template v-slot:activator="{ props }">
                        <v-list-item
                        v-bind="props"
                        :title="com.title"
                        ></v-list-item>
                    </template>

                    <v-list-item
                        v-for="(person, ind) in com.items"
                        :key="ind"
                        :value="person">
                        <v-list-item-title>{{person.name}}</v-list-item-title>
                        <template v-slot:append>
                            <span>{{ person.rate }}</span>
                        </template>
                    </v-list-item>
                </v-list-group>
                
            </v-list> -->
            <v-list lines="three" select-strategy="classic">
                <v-list-subheader class="text-decoration-underline" color="grey-lighten-1">{{com.title}}</v-list-subheader>

                <v-list-item v-for="(person, ind) in com.items"
                        :key="ind">
                    <v-list-item-title>{{person.name}}</v-list-item-title>

                    <v-list-item-subtitle class="d-flex justify-end">
                        {{ person.rate }}
                    </v-list-item-subtitle>
                    <!-- <template v-slot:append>
                            <span>{{ person.rate }}</span>
                        </template> -->
                </v-list-item>
            </v-list>
            <v-divider></v-divider>

        </div>

    </div>

</template>

<script>
export default {
  data () {
    return {
        comp: [
            { title: 'Индивидуальная программа юноши',
              items: [{
                    name: 'Емельянов Александр Андреевич',
                    rate: '10',
                },{
                    name: 'Емельянов Петр Андреевич',
                    rate: '9.9',
                }]
            },
            { title: 'Индивидуальная программа девушки',
                items: [{
                    name: 'Емельянова Анастасия',
                    rate: '10',
                },{
                    name: 'Емельянов Анастасия 2',
                    rate: '9.9',
                }]
            },
        ]
    }
  },
  computed: {
  },
  created() {
    // let comp = this.$store.getters.competitions.find(a => a.id_project.toString() === this.$route.params.id)

  },
}

</script>