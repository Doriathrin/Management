/**
 * 基础菜单 商品管理
 */
<template>
  <div class='goods'>
    <!-- 面包屑导航 -->
      <el-breadcrumb separator-class="el-icon-arrow-right">
        <el-breadcrumb-item :to="{ path: '/' }">一级菜单</el-breadcrumb-item>
        <el-breadcrumb-item>二级菜单</el-breadcrumb-item>
      </el-breadcrumb>
    <!-- 搜索筛选 -->
    <div class='QuestIonnAire'>
      <h3>问卷列表</h3>
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
        <el-form-item label="问卷标题:">
          <el-input v-model="formInline.user"
                    placeholder="请输入"></el-input>
        </el-form-item>
        <el-form-item label="分类:">
          <el-select v-model="formInline.region" value='全部选择'
                    placeholder="请选择">
            <el-option label="全部选择"
                      value="shanghai"></el-option>
            <el-option label="区域二"
                      value="beijing"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="状态:">
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
          <span class="demonstration">修改时间:</span>
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
          <p>问卷页pv</p>
          <p class='sfigure'>5000</p>
        </div>
        <div class="page">
          <p>问卷页uv</p>
          <p class='sfigure'>1000</p>
        </div>
        <div class="page">
          <p>问卷页注册用户pv</p>
          <p class='sfigure'>500</p>
        </div>
        <div class="page">
          <p>问卷页注册用户uv</p>
          <p class='sfigure'>100</p>
        </div>
        <div class="page">
          <p>回收问卷数</p>
          <p class='sfigure'>50</p>
        </div>
        <div class="page">
          <p>回收率</p>
          <p class='sfigure'>50.00%</p>
        </div>
      </div>
    </div>
    <div class='operation'>
      <div class='result'>
        <icon class='icon iconfont'>&#xe66e;</icon>
        <span>查询结果总计:</span>
        <span class='figure'>100</span>
      </div>
      <div class='addition'>
        <el-button type="primary">+新建</el-button>
        <el-button>导出</el-button>
        <el-button>批量删除</el-button>
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
          label="问卷标题"
          width="120">
          <template slot-scope="scope">{{ scope.row.date }}</template>
        </el-table-column>
        <el-table-column
          prop="name"
          label="简介"
          width="120">
        </el-table-column>
        <el-table-column
          prop="address"
          label="图片"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="分类"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="奖励积分"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="已参与/上限人数"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="修改时间"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="状态"
          show-overflow-tooltip>
        </el-table-column>
        <el-table-column
          prop="address"
          label="操作"
          show-overflow-tooltip>
            <span>删除</span>
            <span>编辑</span>
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
// import { deptList, deptSave, deptDelete } from '../../api/userMG'
import { doctor } from '../../api/basisMG'
import Pagination from '../../components/Pagination'
export default {
  data () {
    return {
      formInline: {
        user: '',
        region: ''
      },
      tableData: [{
            date: '2016-05-02',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄'
          }, {
            date: '2016-05-04',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1517 弄'
          }, {
            date: '2016-05-01',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1519 弄'
          }, {
            date: '2016-05-03',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1516 弄'
          }],
      nshow: true, //switch开启
      fshow: false, //switch关闭
      loading: false, //是显示加载
      editFormVisible: false, //控制编辑页面显示与隐藏
      title: '添加',
      editForm: {
        deptId: '',
        deptName: '',
        deptNo: '',
        token: localStorage.getItem('logintoken')
      },
      // rules表单验证
      rules: {
        deptName: [
          { required: true, message: '请输入部门名称', trigger: 'blur' }
        ],
        deptNo: [{ required: true, message: '请输入部门代码', trigger: 'blur' }]
      },
      formInline: {
        page: 1,
        limit: 10,
        varLable: '',
        varName: '',
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
  created () {
    this.getdata(this.formInline)
    this.add();
  },

  /**
   * 里面的方法只有被调用才会执行
   */
  methods: {
    toggleSelection(rows) {
        if (rows) {
          rows.forEach(row => {
            this.$refs.multipleTable.toggleRowSelection(row);
          });
        } else {
          this.$refs.multipleTable.clearSelection();
        }
      },
      handleSelectionChange(val) {
        this.multipleSelection = val;
      },
    onSubmit () {
      console.log('submit!');
    },
    // 获取公司列表
    getdata (parameter) {
      this.loading = true
      // 模拟数据开始
      let res = {
        code: 0,
        msg: null,
        count: 5,
        data: [
          {
            addUser: null,
            editUser: null,
            addTime: 1521062371000,
            editTime: 1526700200000,
            deptId: 2,
            deptName: 'XX分公司',
            deptNo: '1',
            parentId: 1
          },
          {
            addUser: null,
            editUser: null,
            addTime: 1521063247000,
            editTime: 1526652291000,
            deptId: 3,
            deptName: '上海测试',
            deptNo: '02',
            parentId: 1
          },
          {
            addUser: null,
            editUser: null,
            addTime: 1526349555000,
            editTime: 1526349565000,
            deptId: 12,
            deptName: '1',
            deptNo: '11',
            parentId: 1
          },
          {
            addUser: null,
            editUser: null,
            addTime: 1526373178000,
            editTime: 1526373178000,
            deptId: 13,
            deptName: '5',
            deptNo: '5',
            parentId: 1
          },
          {
            addUser: null,
            editUser: null,
            addTime: 1526453107000,
            editTime: 1526453107000,
            deptId: 17,
            deptName: 'v',
            deptNo: 'v',
            parentId: 1
          }
        ]
      }
      this.loading = false
      this.listData = res.data
      this.pageparm.currentPage = this.formInline.page
      this.pageparm.pageSize = this.formInline.limit
      this.pageparm.total = res.count
      // 模拟数据结束

      /***
       * 调用接口，注释上面模拟数据 取消下面注释
       */
      // deptList(parameter)
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
    callFather (parm) {
      this.formInline.page = parm.currentPage
      this.formInline.limit = parm.pageSize
      this.getdata(this.formInline)
    },
    // 搜索事件
    search () {
      this.getdata(this.formInline)
    },
    //显示编辑界面
    handleEdit: function (index, row) {
      this.editFormVisible = true
      if (row != undefined && row != 'undefined') {
        this.title = '修改'
        this.editForm.deptId = row.deptId
        this.editForm.deptName = row.deptName
        this.editForm.deptNo = row.deptNo
      } else {
        this.title = '添加'
        this.editForm.deptId = ''
        this.editForm.deptName = ''
        this.editForm.deptNo = ''
      }
    },
    // 编辑、增加页面保存方法
    submitForm (editData) {
      this.$refs[editData].validate(valid => {
        if (valid) {
          deptSave(this.editForm)
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
              this.$message.error('公司保存失败，请稍后再试！')
            })
        } else {
          return false
        }
      })
    },
    // 删除公司
    deleteUser (index, row) {
      this.$confirm('确定要删除吗?', '信息', {
        confirmButtonText: '确定',
        cancelButtonText: '取消',
        type: 'warning'
      })
        .then(() => {
          deptDelete(row.deptId)
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
              this.$message.error('公司删除失败，请稍后再试！')
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
    closeDialog () {
      this.editFormVisible = false
    },
    add(){
      doctor().then((res)=>{
        console.log(res);
      })
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
.block {
  float: left;
}
.button{
  width: 100%;
  height: 50px;
  margin-top: 10px;
  margin-left: 33px;
}
.QuestIonnAire{
  width: 99%;
  height: 60px;
  line-height: 60px;
  border-top: 2px solid #E6E6E6;
  border-bottom: 2px solid #E6E6E6;
  padding: 0 22px;
  box-sizing: border-box;
  background: white;
  border-radius: 5px;
  margin-left: 13px;
}
.el-breadcrumb{
  width: 99%;
  height: 35px;
  box-sizing: border-box;
  padding: 10px 22px;
  background: white;
  border-radius: 5px;
  margin-top: 1.5px;
  margin-left: 13px;
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
.block{
  margin-left: 30px;
}
.el-form-item{
  margin-left: 31px;
}

.information{
  width: 100%;
  height: 135px;
  background: white;
  margin-top: 10px;
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
</style>

 
 