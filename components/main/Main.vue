<script setup>
const color = ref("indigo");
</script> 
 
<template>
  <v-container>
    <v-row align="center" justify="center">
      <v-col cols="auto">
        <v-radio-group v-model="color" inline>
          <v-row align="center" justify="center">
            <v-col cols="12" max-width="200">
              <v-text-field
                persistent-hint
                placeholder="Ex:3 1"
                v-model.integer="newOrder"
                label="Nova ordem"
              ></v-text-field>
            </v-col>
            <v-col cols="6" align="center" justify="center">
              <v-btn @click="reorderItems()" color="primary">Save</v-btn>
            </v-col>
          </v-row>
        </v-radio-group>
      </v-col>
    </v-row>
    <v-row align="center" justify="center">
      <v-col v-for="(items, index) in items" :key="index" cols="auto">
        <v-card class="mx-auto" max-width="344" :color="color">
          <v-card-item>
            <div>
              <div class="text-overline mb-1"></div>
              <div class="text-h6 mb-1">{{ items.order }}</div>
              <span class="class-period mb-3">
                {{ items.id }}
              </span>
            </div>
          </v-card-item>

          <v-card-actions>
            <v-btn> {{ items.id }} </v-btn>
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
        { order: 1, id: 10 },
        { order: 2, id: 20 },
        { order: 3, id: 30 },
        { order: 4, id: 40 },
        { order: 5, id: 50 },
        { order: 6, id: 60 },
        { order: 7, id: 70 },
        { order: 8, id: 80 },
        { order: 9, id: 90 },
        { order: 10, id: 100 },
      ],

      newOrder: null,
    };
  },
  methods: {
    clearMessage() {
      this.newOrder = "";
    },
    reorderItems() {
      this.newOrder = this.newOrder.split(" ");
      if (this.newOrder[0] > this.newOrder[1]) {
        this.items[this.newOrder[0] - 1].order = this.items[this.newOrder[1] - 1].order;
        this.items[this.newOrder[1] - 1].order = this.items[this.newOrder[1]].order
      } else {
        this.items[this.newOrder[0] - 1].order = this.items[this.newOrder[1]].order;
        this.items[this.newOrder[1]].order++;
      }
      this.items.sort((a, b) => a.order - b.order);
      this.items.forEach((item, index) => {
        item.order = index+1 ;
      });
      this.clearMessage();
    },
  },
};
</script>


