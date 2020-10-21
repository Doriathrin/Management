/**
 * 订单管理 交易订单
 */
<template>
  <div>
    <!-- 面包屑导航 -->
      <el-breadcrumb separator-class="el-icon-arrow-right">
        <el-breadcrumb-item :to="{ path: '/' }">一级菜单</el-breadcrumb-item>
        <el-breadcrumb-item>二级菜单</el-breadcrumb-item>
      </el-breadcrumb>
    <!-- 搜索筛选 -->
    <div class='QuestIonnAire'>
      <h3>用户列表</h3>
    </div>
    <!-- <el-form :inline="true" :model="formInline" class="user-search">
      <el-form-item label="搜索：">
        <el-input size="small" v-model="formInline.deptName" placeholder="输入部门名称"></el-input>
      </el-form-item>
      <el-form-item label="">
        <el-input size="small" v-model="formInline.deptNo" placeholder="输入部门代码"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button size="small" type="primary" icon="el-icon-search" @click="search">搜索</el-button>
        <el-button size="small" type="primary" icon="el-icon-plus" @click="handleEdit()">添加</el-button>
      </el-form-item>
    </el-form> -->
    <div class='form-inline'>
      <el-form :inline="true"
              :model="formInline"
              class="demo-form-inline">
        <el-form-item label="用户id/姓名:">
          <el-input v-model="formInline.user"
                    placeholder="请输入"></el-input>
        </el-form-item>
        <el-form-item label="科室:">
          <el-select v-model="formInline.region" value='全部选择'
                    placeholder="请选择">
            <el-option label="全部选择"
                      value="shanghai"></el-option>
            <el-option label="区域二"
                      value="beijing"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="职称:">
          <el-select v-model="formInline.region"
                    placeholder="请选择">
            <el-option label="全部选择"
                      value="shanghai"></el-option>
            <el-option label="区域二"
                      value="beijing"></el-option>
          </el-select>
        </el-form-item>
      </el-form>
      <el-form :inline="true"
              :model="formInline"
              class="demo-form-inline">
        <div class="block">
          <span class="demonstration">注册时间:</span>
          <el-date-picker
            v-model="value1"
            type="date"
            placeholder="选择日期">
          </el-date-picker>
        </div>
        <div class="block deadline ">
          <span class="demonstration">&nbsp至&nbsp</span>
          <el-date-picker
            v-model="value1"
            type="date"
            placeholder="选择日期">
          </el-date-picker>
        </div>
        <el-form-item label="认证状态:">
          <el-select v-model="formInline.region"
                    placeholder="请选择">
            <el-option label="全部选择"
                      value="shanghai"></el-option>
            <el-option label="区域二"
                      value="beijing"></el-option>
          </el-select>
        </el-form-item>
      </el-form>
      <el-form class='button'>
          <el-button type="primary"
                    @click="onSubmit">查询</el-button>
          <el-button @click="onSubmit">重置</el-button>
      </el-form>
    </div>
    <div class='information'>
      <div class="Categories">
        <div class="page">
          <p>用户数量</p>
          <p class='sfigure'>1000</p>
        </div>
        <div class="page">
          <p>注册人数</p>
          <p class='sfigure'>400</p>
        </div>
        <div class="page">
          <p>认证人数</p>
          <p class='sfigure'>400</p>
        </div>
        <div class="page">
          <p>完成问卷人数</p>
          <p class='sfigure'>500</p>
        </div>
        <div class="page">
          <p>平均完成问卷数</p>
          <p class='sfigure'>2.0</p>
        </div>
        <div class="page">
          <p>平均获得积分数</p>
          <p class='sfigure'>40</p>
        </div>
      </div>
    </div>
    <div class='operation'>
      <div class='result'>
        <icon class='icon iconfont'>&#xe66e;</icon>
        <span>查询结果总计:</span>
        <span class='figure'>36.4万</span>
      </div>
      <div class='addition'>
        <el-button>导出</el-button>
      </div>
    </div>
    <div class='status'>
      <el-table
        ref="multipleTable"
        :data="tableData"
        tooltip-effect="dark"
        style="width: 100%;height:300px"
        @selection-change="handleSelectionChange">
        <el-table-column
          type="selection"
          width="55">
        </el-table-column>
        <el-table-column
          label="用户id"
          align="center"
          width="60">
          <template slot-scope="scope">{{ scope.row.date }}</template>
        </el-table-column>
        <el-table-column
          prop="name"
          label="微信昵称"
          width="110">
        </el-table-column>
        <el-table-column
          prop="address"
          label="姓名"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="性别"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="医院"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="科室"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="职称"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="认证状态"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="完成问卷数"
          width="90"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="获得积分"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="剩余积分"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="修改时间"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="用户状态"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="操作"
          show-overflow-tooltip>
            <span>删除</span>
            <span>审核</span>
        </el-table-column>
      </el-table>
      <el-pagination
        background
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
        :current-page="currentPage4"
        :page-sizes="[10, 20, 30, 40]"
        :page-size="10"
        layout="total, sizes, prev, pager, next, jumper"
        :total="400">
      </el-pagination>
    </div>
  </div>
</template>

<script>
import { OrderList, OrderRefund, OrderDelete } from '../../api/payMG'
import Pagination from '../../components/Pagination'
export default {
  data() {
    return {
      loading: false, //是显示加载
      editFormVisible: false, //控制编辑页面显示与隐藏
      title: '预览',
      payType: [
        { key: '请选择', value: 0 },
        { key: '现金', value: 1 },
        { key: '支付宝', value: 2 },
        { key: '微信', value: 3 },
        { key: 'POS通', value: 4 },
        { key: '闪付', value: 5 },
        { key: 'POS通C扫B', value: 6 },
        { key: '银联二维码', value: 8 },
        { key: '会员余额支付', value: 9 }
      ],
      payway: [
        { key: '请选择', value: 0 },
        { key: '初始化', value: 1 },
        { key: '已支付', value: 2 },
        { key: '出货成功', value: 3 },
        { key: '出货失败', value: 4 },
        { key: '订单超时', value: 5 },
        { key: '退款初始化', value: 11 },
        { key: '退款进行中', value: 12 },
        { key: '退款成功', value: 13 },
        { key: '退款失败', value: 14 },
        { key: '订单处理中', value: 10 }
      ],
      editForm: {
        id: '',
        name: '',
        payType: 1,
        partner: '',
        subMchId: '',
        appid: '',
        notifyUrl: '',
        signType: '',
        partnerKey: '',
        sellerUserId: '',
        certPath: '',
        certPassword: '',
        rsaKey: '',
        token: localStorage.getItem('logintoken')
      },
      formInline: {
        page: 1,
        limit: 10,
        machineNo: '',
        orderNo: '',
        transId: '',
        payType: 0,
        orderStatus: 0,
        token: localStorage.getItem('logintoken')
      },
      // 删除部门
      seletedata: {
        ids: '',
        token: localStorage.getItem('logintoken')
      },
      userparm: [], //搜索权限
      listData: [], //用户数据
      // 分页参数
      pageparm: {
        currentPage: 1,
        pageSize: 10,
        total: 10
      }
    }
  },
  // 注册组件
  components: {
    Pagination
  },
  /**
   * 数据发生改变
   */

  /**
   * 创建完毕
   */
  created() {
    this.getdata(this.formInline)
  },

  /**
   * 里面的方法只有被调用才会执行
   */
  methods: {
    // 获取公司列表
    getdata(parameter) {
      this.loading = true
      // 模拟数据开始
      this.loading = false
      this.listData = res.data
      this.pageparm.currentPage = this.formInline.page
      this.pageparm.pageSize = this.formInline.limit
      this.pageparm.total = res.count
      // 模拟数据结束

      /***
       * 调用接口，注释上面模拟数据 取消下面注释
       */

      // OrderList(parameter)
      //   .then(res => {
      //     this.loading = false
      //     if (res.success == false) {
      //       this.$message({
      //         type: 'info',
      //         message: res.msg
      //       })
      //     } else {
      //       this.listData = res.data
      //       // 分页赋值
      //       this.pageparm.currentPage = this.formInline.page
      //       this.pageparm.pageSize = this.formInline.limit
      //       this.pageparm.total = res.count
      //     }
      //   })
      //   .catch(err => {
      //     this.loading = false
      //     this.$message.error('菜单加载失败，请稍后再试！')
      //   })
    },
    // 分页插件事件
    callFather(parm) {
      this.formInline.page = parm.currentPage
      this.formInline.limit = parm.pageSize
      this.getdata(this.formInline)
    },
    // 搜索事件
    search() {
      this.getdata(this.formInline)
    },
    //显示编辑界面
    handleEdit: function(index, row) {
      this.editFormVisible = true
      this.editForm = row
    },
    // 编辑、增加页面保存方法
    submitForm(editData) {
      this.$refs[editData].validate(valid => {
        if (valid) {
          ConfigSave(this.editForm)
            .then(res => {
              this.editFormVisible = false
              this.loading = false
              if (res.success) {
                this.getdata(this.formInline)
                this.$message({
                  type: 'success',
                  message: '公司保存成功！'
                })
              } else {
                this.$message({
                  type: 'info',
                  message: res.msg
                })
              }
            })
            .catch(err => {
              this.editFormVisible = false
              this.loading = false
              this.$message.error('支付配置信息保存失败，请稍后再试！')
            })
        } else {
          return false
        }
      })
    },
    // 删除公司
    deleteUser(index, row) {
      this.$confirm('确定要删除吗?', '信息', {
        confirmButtonText: '确定',
        cancelButtonText: '取消',
        type: 'warning'
      })
        .then(() => {
          ConfigDelete(row.deptId)
            .then(res => {
              if (res.success) {
                this.$message({
                  type: 'success',
                  message: '公司已删除!'
                })
                this.getdata(this.formInline)
              } else {
                this.$message({
                  type: 'info',
                  message: res.msg
                })
              }
            })
            .catch(err => {
              this.loading = false
              this.$message.error('支付配置信息删除失败，请稍后再试！')
            })
        })
        .catch(() => {
          this.$message({
            type: 'info',
            message: '已取消删除'
          })
        })
    },
    // 关闭编辑、增加弹出框
    closeDialog(formName) {
      this.editFormVisible = false
      this.$refs[formName].resetFields()
    }
  }
}
</script>

<style scoped>
.goods{
  background: #E6E6E6;
}
.user-search {
  margin-top: 20px;
}
.userRole {
  width: 100%;
}
.date{
  /* margin-left: 50px; */
  /* float: left; */
}
.block {
  float: left;
  margin-left: 30px;
}
.button{
  width: 100%;
  height: 50px;
  margin-top: 10px;
  margin-left: 33px;
}
.QuestIonnAire{
  width: 100%;
  height: 60px;
  line-height: 60px;
  border-top: 2px solid #E6E6E6;
  border-bottom: 2px solid #E6E6E6;
  padding: 0 22px;
  box-sizing: border-box;
  background: white;
  border-radius: 5px;
  /* margin-left: 13px; */
}
.el-breadcrumb{
  width: 100%;
  height: 35px;
  box-sizing: border-box;
  padding: 10px 22px;
  background: white;
  border-radius: 5px;
  margin-top: 1.5px;
  /* margin-left: 13px; */
}
.demo-form-inline{
  width: 100%;
  height: 70px;
  /* background: red; */
  line-height: 70px;
  box-sizing: border-box;
  border-radius: 5px;
  /* background: white; */
}
.el-form-item{
  margin-left: 31px;
}

.information{
  width: 100%;
  height: 135px;
  background: white;
  /* margin-top: 10px; */
  border-radius: 5px;
  position: relative;
}
.Categories{
  position: absolute;
  top:0;
  left:0;
  width: 100%;
  height: 110px;
  overflow: hidden;
  /* background: burlywood; */
}

.operation{
  width: 100%;
  height: 130px;
  background: white;
  box-sizing: border-box;
  padding: 10px 20px;
  border-radius: 5px;
  margin-top: 10px;
}
.result{
  width: 90%;
  height: 35px;
  background: #E2F0FA;
  border-radius: 5px;
  border:1px solid #A7D3F1;
  /* box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1); */
  line-height: 35px;
  font-size: 10px;
}
.figure{
  font-weight: 600;
}
.addition{
  margin-top: 20px;
}
.iconfont{
  margin-left: 20px;
}
.form-inline{
  width: 100%;
  height: 200px;
  background: white;
  border-radius: 5px;
  margin-top: 10px;
}
.el-pagination{
  background: white;
  margin-top: 10px;
  margin-left: 200px;
}
.page{
  float: left;
  margin-left: 100px;
  margin-top: 20px;
  text-align: center;
}
.sfigure{
  font-size: 20px;
  margin-top: 30px;
}
.el-table__row{
  background: red;
}
.deadline{
  margin-left: 5px;
}
.status{
  width: 100%;
  height: 360px;
  background: white;
}
.el-table th>.cell{
  padding-left: 15px;
}
</style>

 
 

 