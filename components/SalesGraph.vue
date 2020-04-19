<template>
  <div>
    <v-tabs
      v-model="tab"
    >
      <v-tab :href="'#tab-1'">Casos confirmados</v-tab>
      <v-tab :href="'#tab-2'">Fallecimientos</v-tab>
    </v-tabs>

    <v-tabs-items v-model="tab">
      <v-tab-item :value="'tab-1'">
        <v-card
          class="mx-auto text-center" 
          color="yellow darken-2" 
          dark>
          <v-card-text>
            <v-sheet color="rgba(0, 0, 0, .12)" >
              <v-sparkline
                :value="cases"
                color="yellow lighten-4"
                height="100"
                line-width="1"
                padding= "24"
                stroke-linecap="round"
                smooth= "0"
                :fill= "fill"
                label-size= "8"
              >
                <template v-slot:label="item">
                  {{ item.value }}
                  
                </template>
              </v-sparkline>
            </v-sheet>
          </v-card-text>

          <v-card-text class="text-center">
            <div class="display-1"># Casos confirmados por día</div>
            <div>
              <h2>
                Del {{ initDate }} hasta el {{ finishDate }}
              </h2>
            </div>
          </v-card-text>
        </v-card>
      </v-tab-item>

      <v-tab-item :value="'tab-2'">
        <v-card
          class="mx-auto text-center" 
          color="red darken-3" 
          dark>
          <v-card-text>
            <v-sheet color="rgba(0, 0, 0, .12)" >
              <v-sparkline
                :value="deaths"
                color="red lighten-4"
                height="100"
                line-width="1"
                padding= "24"
                stroke-linecap="round"
                smooth= "0"
                :fill= "fill"
                label-size= "8"
              >
                <template v-slot:label="item">
                  {{ item.value }}
                  
                </template>
              </v-sparkline>
            </v-sheet>
          </v-card-text>

          <v-card-text class="text-center">
            <div class="display-1"># Fallecimientos por día</div>
            <div>
              <h2>
                Del {{ initDate }} hasta el {{ finishDate }}
              </h2>
            </div>
          </v-card-text>
        </v-card>
      </v-tab-item>

    </v-tabs-items>
  </div>
  
</template>

<script>
export default {
  name: 'SalesGraph',
  props: {
    initDate: String,
    finishDate: String,
    cases: {
      type: Array,
      required: true
    },
    deaths: {
      type: Array,
      required: true
    }
  },
  data: () => ({
    tab: null,
    fill: true,
    value: [
      423,
      446,
      675,
      510,
      590,
      610,
      760,
    ],
  })
}
</script>