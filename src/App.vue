<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-menu v-if="state === 2 || state === 3">
        <template v-slot:activator="{ on }">
          <v-btn color="primary lighten-3" v-on="on">
            Item 1
          </v-btn>
        </template>
      </v-menu>

      <v-menu v-if="state === 2 || state === 3">
        <template v-slot:activator="{ on }">
          <v-btn color="primary lighten-1" v-on="on">
            Item 2
          </v-btn>
        </template>
      </v-menu>

      <v-menu v-if="state === 3">
        <template v-slot:activator="{ on }">
          <v-btn color="primary darken-1" v-on="on">
            Item 3
          </v-btn>
        </template>
      </v-menu>

      <v-menu v-if="state === 1 || state === 2">
        <template v-slot:activator="{ on }">
          <v-btn v-on="on">Replacement</v-btn>
        </template>
      </v-menu>
    </v-app-bar>

    <v-btn style="margin-top: 100px" @click="setRandomState">
      Demonstrate Bug
    </v-btn>
  </v-app>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    state: 3,
  }),
  methods: {
    setRandomState() {
      if (this.state === 3) {
        this.state = 1;
      } else if (this.state === 1) {
        this.state = 2;
      } else {
        this.state = 3;
      }
    },
  },
};
</script>
