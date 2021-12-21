<template>
  <div id="parent-block" style="height: 500px">
    <canvas id="matrix"></canvas>
  </div>
</template>

<script>
export default {
  name: "matrix",

  data: () => ({
    parentBlock: null,
    canvasCtx: null,
  }),

  mounted() {
    this.parentBlock = document.getElementById("parent-block")
    window.addEventListener("resize", this.resize);
    this.canvasCore();
  },

  destroyed() {
    window.removeEventListener("resize", this.resize);
  },

  methods: {
    getParentHeight() {
      return this.parentBlock.offsetHeight
    },
    getParentWidth() {
      return this.parentBlock.offsetWidth
    },

    canvasCore() {
      if (this.canvasCtx) {
        setTimeout(() => {

          this.canvasCtx.clearRect(0, 0, 200, 200);
        }, 1)
      }
      let canvas = document.getElementById('matrix');

      let ctx = this.canvasCtx = canvas.getContext('2d');
      let w = canvas.width = this.getParentWidth();
      let h = canvas.height = this.getParentHeight();
      let yPositions = Array(300).join(0).split('');

      function runMatrix() {
        if (typeof interval != 'undefined') clearInterval(interval);
        const interval = setInterval(drawScreen, 30); // 33 оптимально
      }

      function drawScreen () {
        ctx.fillStyle = 'rgba(0,0,0,.05)';
        ctx.fillRect(0, 0, w, h);
        /*
          Неоново-голубой: #04d9ff
          Светлее неоново голубого: #3AE2CE
          Фиолетовый: #FF00AE
          Матрично-зелёный: #0f0
         */
        ctx.fillStyle = '#04d9ff';
        ctx.font = '10px Georgia';
        yPositions.map(function(y, index){
          const text = String.fromCharCode(1e2 + Math.random() * 33);
          const x = (index * 10) + 10;
          ctx.fillText(text, x, y);
          if (y > 100 + Math.random() * 1e4) {
            yPositions[index] = 0;
          } else {
            yPositions[index] = y + 10;
          }
        })
      }
      runMatrix();
    },
    resize() {
      let canvas = document.getElementById('matrix');
      let w = canvas.width = this.getParentWidth();
      let h = canvas.height = this.getParentHeight();
      this.canvasCtx.fillRect(0, 0, w, h);
    }
  },
}
</script>

<style>

</style>