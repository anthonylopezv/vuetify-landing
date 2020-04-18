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
          color="cyan" 
          dark>
          <v-card-text>
            <v-sheet color="rgba(0, 0, 0, .12)">
              <v-sparkline
                :value="value"
                :labels="value"
                color="rgba(255, 255, 255, .7)"
                height="100"
                padding="24"
                stroke-linecap="round"
                smooth
              />
            </v-sheet>
          </v-card-text>

          <v-card-text class="text-center">
            <div class="display-1"># casos confirmados por día</div>
          </v-card-text>
        </v-card>
      </v-tab-item>

      <v-tab-item :value="'tab-2'">
        <v-card
          class="mx-auto text-center" 
          color="teal" 
          dark>
          <v-card-text>
            <v-sheet color="rgba(0, 0, 0, .12)">
              <v-sparkline
                :value="value"
                :labels="value"
                color="rgba(255, 255, 255, .7)"
                height="100"
                padding="24"
                stroke-linecap="round"
                smooth
              />
            </v-sheet>
          </v-card-text>

          <v-card-text class="text-center">
            <div class="display-1"># fallecimientos por día</div>
          </v-card-text>
        </v-card>
      </v-tab-item>

    </v-tabs-items>
  </div>
  
</template>

<script>
export default {
  name: 'SalesGraph',
  data: () => ({
      tab: null,
      value: [
        423,
        446,
        675,
        510,
        590,
        610,
        760,
      ],
    }),
}
</script>