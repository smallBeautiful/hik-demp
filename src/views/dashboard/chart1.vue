<template>
  <div id="c1">hello</div>
</template>

<script>
import G2 from '@antv/g2'

export default {
  name: 'Chart1',
  mounted() {
    this.init()
  },
  methods: {
    init() {
      const data = [
        { genre: 'Sports', sold: 275 },
        { genre: 'Strategy', sold: 115 },
        { genre: 'Action', sold: 120 },
        { genre: 'Shooter', sold: 350 },
        { genre: 'Other', sold: 150 }
      ]
      const chart = new G2.Chart({
        id: 'c1',
        forceFit: true,
        height: 400,
        padding: [40, 80, 100, 80]
      })
      chart.source(data, {
        genre: {
          alias: '游戏种类'
        },
        sold: {
          alias: '销售量',
          min: 0
        }
      })
      chart.coord('polar', {
        innerRadius: 0.6
      })
      chart.axis('genre', {
        label: {
          textStyle: {
            fill: '#f80',
            fontWeight: 'bold'
          }
        }
      })
      chart.interval().position('genre*sold').color('genre')
      chart.render()
    }
  }
}
</script>

<style scoped>

</style>

