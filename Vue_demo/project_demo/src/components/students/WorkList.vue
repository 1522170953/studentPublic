<template>
  <div class="workList">
    <el-table :data="tableData" v-loading="loading" border style="width: 100%">
      <el-table-column prop="id" label="用户ID" align="center">
      </el-table-column>
      <el-table-column prop="userId" label="所属班级" align="center">
      </el-table-column>
      <el-table-column prop="title" label="作业名称" align="center">
      </el-table-column>
      <el-table-column prop="completed_txt" label="完成情况" align="center">
      </el-table-column>
    </el-table>
    <el-pagination
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
      :current-page="page"
      :page-sizes="[5, 10, 50, 100]"
      :page-size="size"
      layout="total, sizes, prev, pager, next, jumper"
      :total="total"
    >
    </el-pagination>
  </div>
</template>

<script>
import { getTableData } from "@/utils/table";

export default {
  name: "WorkListView",
  data() {
    return {
      tableData: [],
      total:0,
      page:1,
      size:10,
      loading:true
    };
  },
  methods: {
    //   分页
    handleSizeChange(val) {
      this.size = val;
      this.page = 1;
      console.log(`每页 ${val} 条`);
    getTableData(this, "/works", {page: this.page ,size:val} ,["completed", "id"]);
    },
    handleCurrentChange(val) {
      this.page = val;
      console.log(`当前页: ${val}`);
    getTableData(this, "/works", {page: val ,size:this.size} ,["completed", "id"]);
    },
  },
  created() {
    getTableData(this, "/works", {page: this.page ,size:this.size} ,["completed", "id"]);
  },
};
</script>

<style lang="scss" scoped>
.workList{
    .el-pagination{
        text-align: left;
        margin-top: 20px;
    }
}

</style>
