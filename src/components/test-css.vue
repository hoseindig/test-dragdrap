<template>
  <div>
    <!-- <v-row>
      <v-col class="col-md-6">
        <v-text-field label="نام"> </v-text-field>
      </v-col>
    </v-row> -->
    {{ sliderX }}
    {{ sliderY }}
    <p>sliderDXNum x :{{ obj.x }} y :{{ obj.y }}</p>
    <v-row>
      <v-col cols="12">
        <v-slider
          max="1000"
          min="150"
          v-model="sliderXNum"
          thumb-label
        ></v-slider>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <v-slider
          max="1000"
          min="150"
          v-model="sliderYNum"
          thumb-label
        ></v-slider>
      </v-col>
    </v-row>
    <v-layout justify-center>
      <v-flex md5>
        <v-text-field
          href="#none"
          label="نام"
          :style="{ ...style, left: sliderX, top: sliderY }"
        />
        <input
          type="text"
          @click="calcPosOfBox"
          ref="my_box_a"
          value=""
          placeholder="نام"
          :style="{ ...style }"
        />
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
export default {
  data() {
    return {
      sliderXNum: 45,
      sliderYNum: 45,
      obj: {
        x: null,
        y: null,
      },

      //   items: [
      //     {
      //       key: "1",
      //       name: "name",
      //       text: "نام",
      style: {
        position: "absolute",
        "font-size": "30px",
        // left: "130px",
        // top: "30px",
      }, //'background-color':'red'
      // },
      //   ],
    };
  },
  methods: {
    calcPosOfBox() {
      this.obj.x = this.$refs["my_box_a"].getBoundingClientRect().x;
      this.obj.y = this.$refs["my_box_a"].getBoundingClientRect().y;
      //   this.posBoxB = this.$refs["my_box_b"].getBoundingClientRect().x;
    },
    getPos() {
      this.obj.x = this.$refs.busstop.getBoundingClientRect().left;
      this.obj.y = this.$refs.busstop.getBoundingClientRect().top;
    },
  },
  computed: {
    sliderX() {
      return this.sliderXNum + "px";
    },
    sliderY() {
      return this.sliderYNum + "px";
    },
  },
};
</script>
