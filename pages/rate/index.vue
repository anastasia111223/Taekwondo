<template>
    <div class="pa-10">
        <div class="d-flex justify-space-between">
            <div class="d-flex flex-column justify-center">
                <h3>{{`Выступление участника:`}}</h3>
                <h3 v-if="competitor.name">{{competitor.name}}</h3>
                <h4 v-if="competitor.name">{{competitor.age}}</h4>
            </div>
            <div class="d-flex justify-end" >
                <v-btn variant="text" rounded="lg" height="30px"
                @click="sendCount()">
                <span>Отправить оценку</span>
                </v-btn>
            </div>
        </div>
        <div class="d-flex justify-center">
            <h2 class="text-h3 text-md-h2 text-lg-h1">{{count}}</h2>
        </div>
        <v-row class="d-flex justify-space-between">
            <v-col cols="4"  class="pa-0">
                <span class="text-grey">{{`(-0.3)*${count03}`}}</span>
            </v-col>
            <v-col cols="4" class="d-flex justify-end pa-0">
                <span color="info">{{`(-0.1)*${count01}`}}</span>
            </v-col>
        </v-row>
        <v-row class="py-5 d-flex justify-space-between">
            <v-col cols="5">
                <v-btn variant="outlined" block rounded="lg" size="x-large" color="red" height="250px"
                @click="editCount2()">
                <span class="text-">-0.3</span>
                </v-btn>
            </v-col>
            <v-col cols="5">
                <v-btn variant="outlined" block rounded="lg" size="x-large" color="yellow" height="250px"
                @click="editCount1()">
                <span class="text-h5 text-md-h4 text-lg-h3">-0.1</span>
                </v-btn>
            </v-col>
        </v-row>
        <v-row class="pt-15 d-flex justify-center">
            <v-col md="6" xs="12" s="12">
                <h2 class="d-flex justify-center">{{`Представление: ${power+speed+energy}`}}</h2>
                <v-slider
                    v-model="power"
                    step="0.1"
                    label="Скорость и сила"
                    ticks
                    max="2"
                    min="0.5"
                    class="pt-6"
                    thumb-label="always">
                    <template v-slot:append>
                    <p>2</p>
                    <!-- <v-text-field
                        class="mt-0 pt-0"
                        type="number"
                        style="width: 60px"
                    >7</v-text-field> -->
                    </template>
                </v-slider>
                <v-slider
                    v-model="speed"
                    step="0.1"
                    label="Скорость и ритм"
                    ticks
                    max="2"
                    min="0.5"
                    class="pt-7"
                    thumb-label="always">
                    <template v-slot:append>
                    <p>2</p>
                    <!-- <v-text-field
                        class="mt-0 pt-0"
                        type="number"
                        style="width: 60px"
                    >7</v-text-field> -->
                    </template>
                </v-slider>
                <v-slider
                    v-model="energy"
                    step="0.1"
                    label="Выражение энергии"
                    ticks
                    max="2"
                    min="0.5"
                    class="pt-7"
                    thumb-label="always">
                    <template v-slot:append>
                    <p>2</p>
                    <!-- <v-text-field
                        class="mt-0 pt-0"
                        type="number"
                        style="width: 60px"
                    >7</v-text-field> -->
                    </template>
                </v-slider>
            </v-col>
            
        </v-row>

    </div>

</template>

<script>
export default {
  data () {
    return {
        competitor: {
            name: "Емельянов Александр Андреевич",
            age: '9 лет',
        },
        today: '',
        count: 4,
        count01: 0,
        count03: 0,
        power: 2,
        speed: 2,
        energy: 2,
    }
  },
  computed: {
    present() {
        return Math.floor((this.power + this.speed + this.energy)*10)/10
    }
  },
  methods: {
    editCount1() {
        if (this.count===0.3) {
            this.count = 0.2;
            this.count01 ++;
        } else if (this.count>=0.1) {
            this.count = Math.floor((this.count - 0.1)*10)/10;
            this.count01 ++;
        }
    },
    editCount2() {
        if (this.count>=0.3) {
            this.count = Math.floor((this.count - 0.3)*10)/10;
            this.count03 ++;
        }
    },
    sendCount() {
        
    },
  },
  created() {
    // if (!this.$store.getters.competors) {

    // }
    // this.competitor = this.$store.getters.competors.find(a => a.id_project.toString() === this.$route.params.id);
    // if (!this.competitor) {
    //     this.competitor.name = "Емельянов Александр Андреевич";
    //     this.competitor.age = '9 лет'
    // }
  },
}

</script>