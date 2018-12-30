<template>
 <div class="rushWater">
        <div class="ctrlPress">
            <div class="title2" style="margin-bottom:10px;">
               <div class="presurecontrolarea"> 压力控制点压力</div>
                <div class="btn-wrapper">
                    <div class="btn" @click="HandleAdd"><i class="add"></i><span>添加</span></div>
                </div>

            </div>
            <el-table
                ref="ctrlPressTable" stripe
                :data="ylkzTable"
                height="170px"
                style="width: 100%"
               >
                <el-table-column
                    label="编号"
                    prop="CodeId">
                </el-table-column>
                <el-table-column
                    prop="PressureName"
                    label="压力点名称">
                </el-table-column>
                <el-table-column
                    prop="CtPressure"
                    label="目标压力(MPa)">
                </el-table-column>
                <el-table-column
                 label="操作">
                  <template slot-scope="scope">
                      <div class="deleteBtn" @click="Handledelete(scope.$index, scope.row)"></div>
                  </template>
                </el-table-column>
            </el-table>
        <div class="fyoutbox">
            <div class="totalnum">共<span>{{ylkzTable.length}}</span>条</div>
            <div class="fybutton">
                 <div class="block">
                    <el-pagination
                    @current-change="handleCurrentChange"
                    :page-size="5"
                    layout="prev, pager, next"
                    :total="ylkzTable.length">
                    </el-pagination>
                 </div>
            </div>
        </div>
        </div>

        <!-- 弹出层 -->
        <el-dialog title="压力控制点添加" :visible.sync="dialogVisible" custom-class="inner-lay" width="384px" modal modal-append-to-body close-on-click-modal center>
            <el-form :model="form" label-position="left">
                <el-form-item label="压力控制点名称" :label-width="formLabelWidth">
                    <el-select v-model="form.pressValue" @change="HandleValueChange">
                        <el-option
                            v-for="item in addOptions"
                            :key="item.CodeId"
                            :label="item.PressureName"
                            :value="item.CodeId">
                        </el-option>
                    </el-select>
                </el-form-item>
                <el-form-item label="目标压力" :label-width="formLabelWidth">
                    <el-input v-model="form.target" class="input" @change="HandleInputValue"> <template slot="append">MPa</template></el-input>
                </el-form-item>
            </el-form>
            <div slot="footer" class="dialog-footer" style="text-align:center;">
                <el-button type="primary" @click.native="addOne">确 定</el-button>
                <el-button @click="dialogVisible = false">取 消</el-button>
            </div>
        </el-dialog>

    </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
        currentPage1: 5,
      form: {
        pressValue: "请选择",
        target: 0
      },
      selectedOption: {}, //添加的对象
      formLabelWidth: "100px",
      baseInfo: {},
      gsl: " ",
      dialogVisible: false,
      WaterData: [],
      ylkzTable: [
        { CodeId: 1101, PressureName: 0.123, CtPressure: 163 },
        { CodeId: 1102, PressureName: 0.124, CtPressure: 723 },
        { CodeId: 1103, PressureName: 0.124, CtPressure: 823 },
        { CodeId: 1104, PressureName: 0.125, CtPressure: 923 },
        { CodeId: 1106, PressureName: 0.127, CtPressure: 193 },
        { CodeId: 1107, PressureName: 0.128, CtPressure: 183 },
        { CodeId: 1108, PressureName: 0.129, CtPressure: 163 },
        { CodeId: 1109, PressureName: 0.131, CtPressure: 125 },
        { CodeId: 1110, PressureName: 0.133, CtPressure: 123 },
        { CodeId: 1111, PressureName: 0.143, CtPressure: 153 }
      ],
      pressTable: [],
      page_total: 0,
      currentPage: 1,
      pageSize: 5,
      addOptions: [], // 添加按钮数据
      curCodeId: "", //当前codeId
      headerStyle() {
        return {
          height: "40px",
          "line-height": "40px",
          "background-color": "#f0f0f1",
          color: "#778392"
        };
      },
      rowStyle() {
        return {
          height: "40px",
          "line-height": "40px",
          color: "#6e7b8b"
        };
      },
       currentPage: 1, //默认显示第一页
      pageSize: 5 ,//默认每页显示10条
       info: [],
    };
    
  },
   created() {
    this.info = this.ylkzTable.slice(0, 5);
  },
  methods: {
     handleCurrentChange(val) {
      console.log(`当前页: ${val}`);
      this.info = this.ylkzTable.slice(5* val - 5, 5* val);
    },
    Handledelete(index, row) {
      this.ylkzTable.splice(index, 1);
      var objectTemp = {
        pressPointList: this.ylkzTable,
        pressCtrlList: this.ylkzTable
      };
      WindowsEvent.MyDispatchEvent(
        "EmergencyDispatchPressureNodePosition",
        objectTemp
      );
    },
    HandleAdd() {
      this.dialogVisible = true;
      this.ajaxOverLayData();
    },
    handleCurrentChange(val) {
      this.currentPage = val;
    },
    HandleValueChange(v) {
      let self = this;
      this.curCodeId = v;
      this.addOptions.forEach(function(ele, index) {
        if (ele.CodeId === v) {
          self.form.target = ele.CtPressure;
          self.selectedOption = ele || {};
        }
      });
    },
    HandleInputValue(v) {
      this.selectedOption.CtPressure = v;
    },
    addOne() {
      this.dialogVisible = false;
      this.ylkzTable.push(this.selectedOption);
      var objectTemp = {
        pressPointList: this.ylkzTable,
        pressCtrlList: this.ylkzTable
      };
      WindowsEvent.MyDispatchEvent(
        "EmergencyDispatchPressureNodePosition",
        objectTemp
      );
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
.rushWater {
  height: 100%;
  width: 60%;
  margin: 0 500px;
  .ctrlPress {
    /*  padding: 10px 20px;*/
    /*    border-bottom: 1px solid #d1d1da;  */
    .presurecontrolarea {
    }
    .btn-wrapper {
      float: right;
      .btn {
        display: inline-block;
        color: #6e7b8b;
        height: 13px;
        line-height: 13px;
        cursor: pointer;
        i {
          display: inline-block;
          margin-right: 5px;
          vertical-align: top;
          &.add {
            width: 13px;
            height: 13px;
            background: url("../assets/add.png") no-repeat;
          }
          &.save {
            width: 12px;
            height: 12px;
            background: url("../assets/save.png") no-repeat;
          }
        }
        span {
          display: inline-block;
          vertical-align: top;
        }
      }
    }
  }
}
</style>
<style lang="less" scoped>
.title2 {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: space-between;
  align-items: flex-start;
  width: 100%;
  margin-bottom: 10px;
  height: 40px;
  line-height: 40px;
  border-bottom: 1px solid #d1d1da;
}
.deleteBtn {
  width: 12px;
  height: 16px;
  background: url("../assets/delete.png") no-repeat;
  cursor: pointer;
}
.rushWater {
  .pagination-wrapper {
    height: 40px;
    border-top: 1px solid #d1d1da;
    box-sizing: border-box;
    padding: 0 20px;
    .el-pagination {
      padding-top: 6px;
      box-sizing: border-box;
      display: inline-block;
      float: right;
    }
  }
}
.inner-lay {
  .el-input__inner {
    width: 180px;
    background: #f0f0f1;
    border: none;
  }
  .input {
    .el-input__inner {
      width: 135px;
      margin-right: 0px;
    }
    .el-input-group__append {
      background-color: #fff;
      color: #808891;
      vertical-align: middle;
      display: table-cell;
      position: relative;
      border: none;
      padding: 0 55px 0 0;
      white-space: nowrap;
    }
  }
}
</style>
