<template>
  <div id="graph">
  </div>
</template>

<script>
import ForceGraph3D from '3d-force-graph';
export default {
  el: '#hello',
  mounted() {
    const g = ForceGraph3D()(document.getElementById('graph'))
    const N = 300;
    const gData = {
      nodes: [...Array(N).keys()].map(i => ({ id: i })),
      links: [...Array(N).keys()]
          .filter(id => id)
          .map(id => ({
            source: id,
            target: Math.round(Math.random() * (id-1))
          }))
    };
    g.graphData(gData);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
