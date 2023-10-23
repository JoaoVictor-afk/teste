<script setup>

// const variants = ["elevated", "flat", "tonal", "outlined"];
 const color = ref("indigo");
</script> 
 
 <template>
  <v-container>
    <v-row align="center" justify="center">
      <v-col cols="auto">
        <v-radio-group v-model="color" inline>
          <v-radio label="indigo" color="indigo" value="indigo"></v-radio>
          <v-radio
            label="indigo-darken-3"
            color="indigo-darken-3"
            value="indigo-darken-3"
          ></v-radio>
          <v-radio label="primary" color="primary" value="primary"></v-radio>
          <v-radio
            label="secondary"
            color="secondary"
            value="secondary"
          ></v-radio>
        </v-radio-group>
      </v-col>
    </v-row>
    <v-row align="center" justify="center">
      <v-col v-for="(items, order) in items" :key="order" cols="auto">
        <v-card
          class="mx-auto"
          max-width="344"
          :color="color"
          :variant="variant"
        >
          <v-card-item>
            <div>
              <div class="text-overline mb-1">
              </div>
              <div class="text-h6 mb-1">{{items.order}} </div>
              <span class="class-period mb-3">
                {{items.color}}
          </span>
            </div>
          </v-card-item>

          <v-card-actions>
            <v-btn> {{items.color}} </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>

export default {
  name: "Main",

  data() {
    return {
      items: [
        { order: 1, color: `white` },
        { order: 2, color: 'black' },
        { order: 3, color: 'white' },
        { order: 4, color: 'black' },
        { order: 5, color: 'white' },
      ],
    };
  },
};
</script>
