<template>
  <div class="measure">
    <!-- 页面标识 -->
    <div class="pages">
      <div class="h3">数据实体/规则定义</div>
      <div>
        <span class="span_size">TPAS-ZYRY</span>
      </div>
    </div>
    <!-- 表格 -->
    <div class="content">
        <el-table
          ref="singleTable"
          :data="tableData"
          highlight-current-row
          @current-change="handleCurrentChange"
          style="width: 100%"
          height="480">
          <el-table-column
            type="index"
            width="50">
          </el-table-column>
          <el-table-column
            property="date"
            label="字段名"
            width="250">
          </el-table-column>
          <el-table-column
            property="name"
            label="类型"
            width="250">
          </el-table-column>
          <el-table-column
            property="address"
            label="规则定义">
            <el-select v-model="address" placeholder="默认无需检测">
                <el-option
                  v-for="item in options"
                  :key="item.value"
                  :label="item.label"
                  :value="item.value">
                </el-option>
            </el-select>
          </el-table-column>
        </el-table>
    </div>
    <!-- 操作 -->
    <div class="pagination_parent">
      <div class="pagination">
        <el-button-group>
          <el-button type="primary" icon="el-icon-upload">提交</el-button>
        </el-button-group>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      tableData: [{
        date: 'ID',
        name: 'string',
        address: '无需检测'
      },
      {
        date: 'Orgnization',
        name: 'string',
        address: '无需检测'
      },
      {
        date: 'Orgname',
        name: 'string',
        address: '无需检测'
      },
      {
        date: 'UserID',
        name: 'string',
        address: '无需检测'
      }],
      options: [{
        value: '选项1',
        label: '无需检测'
      }, {
        value: '选项2',
        label: '标准化检查'
      }, {
        value: '选项3',
        label: '完整性检查'
      }, {
        value: '选项4',
        label: '标准化检查'
      }, {
        value: '选项5',
        label: '奇异值检查'
      }],
      value: '',
      currentRow: null
    }
  },
  methods: {
    setCurrent (row) {
      this.$refs.singleTable.setCurrentRow(row)
    },
    handleCurrentChange (val) {
      this.currentRow = val
    }
  }
}
</script>
<style scoped>
.measure {
  padding: 10px;
}
.pages {
  padding: 10px;
  border-radius: 4px;
  background-color: white;
  margin-bottom: 10px;
  margin-top: 60px;
  height: 90px;
}
.h3 {
  font-size: 14px;
  font-weight: bold;
  margin-bottom: 8px;
  color:#909399;
}
.span_size {
  font-size: 20px;
  color: #303133;
}
.pagination_parent {
  background: white;
  border-radius: 4px;
}
.pagination {
  padding: 5px;
  border-radius: 4px;
  width: 90px;
  margin: 5px auto;
}
</style>
