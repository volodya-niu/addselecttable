<template>
  <div class="hello">
         <div class="outbox">
        <div class="inbox1">
            <div style=" width:11%;height:20px;background-color:#ededef;line-height:20px;text-align:start;margin-left:5px">水厂名称</div>
            <div style=" width:11%;height:20px;line-height:20px;text-align:start;margin-left:5px">出厂压力</div>
            <div style=" width:11%;height:20px;line-height:20px;text-align:start;margin-left:5px">出厂流量</div>
            <div style=" width:11%;height:20px;line-height:20px;text-align:start;margin-left:5px">清水池水位</div>
             <div style=" width:7%;height:20px;line-height:20px;text-align:start;margin-left:5px">1#</div>
            <div style=" width:7%;height:20px;line-height:20px;text-align:start;margin-left:5px">2#</div>
            <div style=" width:7%;height:20px;line-height:20px;text-align:start;margin-left:5px">3#</div>
            <div style=" width:7%;height:20px;line-height:20px;text-align:start;margin-left:5px">4#</div>
             <div style=" width:7%;height:20px;line-height:20px;text-align:start;margin-left:5px">5#</div>
            <div style=" width:7%;height:20px;line-height:20px;text-align:start;margin-left:5px">6#</div>
            <div style=" width:7%;height:20px;line-height:20px;text-align:start;margin-left:5px">7#</div>
            <div style=" width:7%;height:20px;line-height:20px;text-align:start;margin-left:5px">8#</div>
        </div>
        <div class="inbox2" v-for="(item,index) in stu" :key="index" style="border-bottom:1px solid #ededed;">  
            <div style="display:flex;flex-direction:row;">
              <div style="color:#000;width:105px;height:30px;line-height:30px;text-align:start;font-size:12px;margin-left:5px">{{item.WaterworksName}}</div>
              <div style="color:#000;width:105px;height:30px;line-height:30px;text-align:start;font-size:12px;margin-left:5px">{{item.OutPressure}}</div>
              <div style="color:#000;width:105px;height:30px;line-height:30px;text-align:start;font-size:12px;margin-left:5px">{{item.OutFlow}}</div>
              <div style="color:#000;width:95px;height:30px;line-height:30px;text-align:start;font-size:12px;margin-left:5px">{{item.ClearWaterLevel}}</div>
              <div class="bgbox" v-for="(items,indexs) in item.PumpList" :key="indexs" :class="stu[index].PumpList[indexs].OpenCloseType==1? 'nowclose' :(stu[index].PumpList[indexs].OpenCloseType==2? 'nowmissingdata' :(stu[index].PumpList[indexs].OpenCloseType==3? 'nowopen' :(stu[index].PumpList[indexs].OpenCloseType==4? 'nowopendingbeng' :'')))">{{items.Speed}}</div>
            </div>
      </div>
    </div>
    </div>
</template>
<script>
export default {
  name: "table3",
  data() {
    return {
      stu: [{
    "ClearWaterLevel": 3.9091,
    "OutFlow": 19615.2109,
    "OutPressure": 0.3585,
    "PumpList": [{
      "AdjustmentType": 0,
      "OpenCloseType": 3,
      "PumpNo": 1,
      "Speed": "728"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 2,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 1,
      "PumpNo": 3,
      "Speed": "OFF"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 1,
      "PumpNo": 4,
      "Speed": "OFF"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 3,
      "PumpNo": 5,
      "Speed": "723"
    }],
    "WaterworksName": "笔架山水厂"
  }, {
    "ClearWaterLevel": 4.2667,
    "OutFlow": 14230.8105,
    "OutPressure": 0.4396,
    "PumpList": [{
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 1,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 1,
      "PumpNo": 2,
      "Speed": "OFF"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 3,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 4,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 5,
      "Speed": "ON"
    }],
    "WaterworksName": "大涌北水厂"
  }, {
    "ClearWaterLevel": 5.0969,
    "OutFlow": 5631.9214,
    "OutPressure": 0.4293,
    "PumpList": [{
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 1,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 1,
      "PumpNo": 2,
      "Speed": "OFF"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 3,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 4,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 1,
      "PumpNo": 5,
      "Speed": "OFF"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 1,
      "PumpNo": 6,
      "Speed": "OFF"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 7,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 8,
      "Speed": "ON"
    }],
    "WaterworksName": "大涌南水厂"
  }, {
    "ClearWaterLevel": 3.4449,
    "OutFlow": 18853,
    "OutPressure": 0.3834,
    "PumpList": [{
      "AdjustmentType": 0,
      "OpenCloseType": 1,
      "PumpNo": 1,
      "Speed": "OFF"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 2,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 3,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 4,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 5,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 6,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 7,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 8,
      "Speed": "ON"
    }],
    "WaterworksName": "东湖水厂"
  }, {
    "ClearWaterLevel": 9.1194,
    "OutFlow": 32301,
    "OutPressure": 0.2903,
    "PumpList": [{
      "AdjustmentType": 0,
      "OpenCloseType": 1,
      "PumpNo": 1,
      "Speed": "OFF"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 3,
      "PumpNo": 2,
      "Speed": "539"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 3,
      "PumpNo": 3,
      "Speed": "541"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 1,
      "PumpNo": 4,
      "Speed": "OFF"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 1,
      "PumpNo": 5,
      "Speed": "OFF"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 6,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 1,
      "PumpNo": 7,
      "Speed": "OFF"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 8,
      "Speed": "ON"
    }],
    "WaterworksName": "梅林水厂"
  }, {
    "ClearWaterLevel": 5.4063,
    "OutFlow": 12145.5439,
    "OutPressure": 0.3771,
    "PumpList": [{
      "AdjustmentType": 0,
      "OpenCloseType": 1,
      "PumpNo": 1,
      "Speed": "OFF"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 3,
      "PumpNo": 2,
      "Speed": "951"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 3,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 4,
      "PumpNo": 4,
      "Speed": "ON"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 3,
      "PumpNo": 5,
      "Speed": "948"
    }, {
      "AdjustmentType": 0,
      "OpenCloseType": 1,
      "PumpNo": 6,
      "Speed": "OFF"
    }],
    "WaterworksName": "南山水厂"
  }]
    };
  },


};
</script>
<style scoped>
.outbox{

  width: 1000px;
  height: 100%;

}
.inbox1{
   width: 1000px;
    display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: flex-start;
  background-color:#ededef;
  font-size:12px;
  
}
.bgbox{
    height:30px;
    line-height:30px;
    width:65px;
    border-left:1px solid #ededed;
    text-align:start;
    font-size:12px;
    margin-left:5px
}
.nowmissingdata {
     height:30px;
    line-height:30px;
    width:65px;
    margin-left:5px;
      background-color: red;
}
.nowclose {
     height:30px;
    line-height:30px;
    width:65px;
    margin-left:5px;
  background-color: #b81616;

}
.nowopen {
     height:30px;
    line-height:30px;
    width:65px;
    margin-left:5px;
  background-color: #abe931;
 
}
.nowopendingbeng {
     height:30px;
    line-height:30px;
    width:65px;
  background-color: #abe931;

}
</style>
