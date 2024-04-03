<template>
  <div class="title">資金費率機器人 by 呢喃貓</div>
  <el-table :data="results" :default-sort="{ prop: 'APY', order: 'ascending' }" stripe style="width: 100%">
    <el-table-column label="交易兌" width="180">
      <template #default="scope">
        <div style="display: flex; align-items: center">
          <span style="margin-left: 10px">{{ scope.row.symbol }}</span>
        </div>
      </template>
    </el-table-column>
    <el-table-column label="現貨" width="180">
      <template #default="scope">
        <div>{{ scope.row.spotExchange }}</div>
        <div>${{ scope.row.spotPrice }}</div>
      </template>
    </el-table-column>
    <el-table-column label="合約" width="180">
      <template #default="scope">
        <div>{{ scope.row.exchange }}</div>
        <div>${{ scope.row.indexPrice }}</div>
      </template>
    </el-table-column>
    <el-table-column prop="priceGap" label="點差" width="180"></el-table-column>
    <el-table-column prop="fundingRate" label="資金費率" width="180"></el-table-column>
    <el-table-column label="APY(%)" sortable width="180">
      <template #default="scope">
        <div>{{ scope.row.APY }}%</div>
      </template>
    </el-table-column>
    <el-table-column prop="volume" label="交易量(M)" sortable width="180"></el-table-column>
  </el-table>
</template>

<script>
import db from '../firebaseInit'
import { collection, getDocs } from 'firebase/firestore/lite'

export default {
  data() {
    return {
      results: [],
      fields: ['exchange', 'symbol', 'fundingRate']
    }
  },
  methods: {
    async readFilteredResult() {
      const filteredCol = collection(db, 'filtered_result')
      const resultSnapshot = await getDocs(filteredCol)
      const resultList = resultSnapshot.docs.map((doc) => {
        this.results.push({
          id: doc.id,
          symbol: doc.data().symbol,
          APY: Math.round(doc.data().APY * 100) / 100,
          exchange: doc.data().exchange,
          fundingRate: doc.data().fundingRate,
          fundingRate_1day_avg: doc.data().fundingRate_1day_avg,
          indexPrice: Math.round(doc.data().indexPrice * 10000) / 10000,
          markPrice: doc.data().markPrice,
          order: doc.data().order,
          preFundingRate: doc.data().preFundingRate,
          priceGap: Math.round(doc.data().priceGap * 10000) / 10000,
          spotExchange: doc.data().spotExchange,
          spotPrice: Math.round(doc.data().spotPrice * 10000) / 10000,
          volume: Math.round(doc.data().volume / 1000000 * 100) / 100
        })
      })
    }
  },
  mounted() {
    this.readFilteredResult()
  }
}
</script>

<style>
  .title {
    text-align: left;
    color: white;
    font-size: 35px;
    background: gray;
  }
</style>