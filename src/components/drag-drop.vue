<template>
  <div>
    <p style="position: absolute; bottom: 0px">
      cordX : {{ cordX }} - cordY: {{ cordY }}
    </p>
    <h1>drag drop</h1>
    <div id="mydiv" :style="{ top: cordY + 'px', left: cordX + 'px' }">
      <p>X : {{ cordX }} - Y: {{ cordY }}</p>

      <div
        id="mydivheader"
        draggable="true"
        @drag="dragging"
        @dragstart="dragStart(1, $event)"
        @dragover.prevent
        @dragenter="dragEnter"
        @dragleave="dragLeave"
        @dragend="dragEnd"
        @drop="dragFinish(1, $event)"
      >
        DRAG
      </div>
      <input type="text" placeholder="text box 1" />
      <input type="text" placeholder="text box 2" />
      <input type="text" placeholder="text box 3" />
      <!-- <p>BLA</p> -->
    </div>
  </div>
</template>

<script>
const offset = {
  x: 50,
  y: 100,
};
export default {
  data() {
    return {
      cordY: 0,
      cordX: 0,
    };
  },
  methods: {
    dragging: function (e) {
      let obj = {
        x: e.clientY,
        y: e.clientX,
      };
      console.log("dragging ", obj.x, obj.y);
      // eslint-disable-next-line no-debugger
      //   debugger;

      this.cordY = e.clientY - offset.y;
      this.cordX = e.clientX - offset.x;
    },

    dragStart(e) {
      console.log("dragStart");
      let obj = {
        x: e.clientY,
        y: e.clientX,
      };
      console.log("dragStart ", obj.x, obj.y);

      //   ev.dataTransfer.setData("Text", this.id);
      //   ev.dataTransfer.dropEffect = "move";
      //   this.dragging = which;
    },
    dragEnter(e) {
      // eslint-disable-next-line no-debugger
      console.log("dragEnter");
      let obj = {
        x: e.clientY,
        y: e.clientX,
      };
      console.log("dragEnter ", obj.x, obj.y);
      /* 
      if (ev.clientY > ev.target.height / 2) {
        ev.target.style.marginBottom = '10px'
      } else {
        ev.target.style.marginTop = '10px'
      }
      */
    },
    dragLeave(e) {
      // eslint-disable-next-line no-debugger
      //   debugger;
      console.log("dragLeave");
      let obj = {
        x: e.clientY,
        y: e.clientX,
      };
      console.log("dragLeave ", obj.x, obj.y);
      /* 
      ev.target.style.marginTop = '2px'
      ev.target.style.marginBottom = '2px'
      */
    },
    dragEnd(e) {
      console.log("dragEnd");
      let obj = {
        x: e.clientY,
        y: e.clientX,
      };
      console.log("dragEnd ", obj.x, obj.y);
      this.cordY = e.clientY - offset.y;
      this.cordX = e.clientX - offset.x;
      // eslint-disable-next-line no-debugger
      //   debugger;
      //   this.dragging = -1;
    },
    dragFinish(e) {
      // eslint-disable-next-line no-debugger
      //   debugger;
      console.log("dragFinish");
      let obj = {
        x: e.clientY,
        y: e.clientX,
      };
      console.log("dragFinish ", obj.x, obj.y);
      //   this.moveItem(this.dragging, to);
      //   ev.target.style.marginTop = "2px";
      //   ev.target.style.marginBottom = "2px";
    },
  },
};
</script>

<style scoped>
#mydiv {
  position: absolute;
  width: 150px;
  z-index: 9;
  background-color: #f1f1f1;
  border: 1px solid #d3d3d3;
  text-align: center;
}

#mydivheader {
  padding: 10px;
  cursor: move;
  z-index: 10;
  background-color: #2196f3;
  color: #fff;
}
</style>


