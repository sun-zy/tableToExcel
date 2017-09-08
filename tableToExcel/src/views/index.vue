<style lang="sass" >
    .con {
        width: 100%;
        height: 100%;
        padding: 0 20px;
        display: inline-block;
        /* loading样式 */
        .demo-spin-icon-load{
            animation: ani-demo-spin 1s linear infinite;
            font-size: 40px!important;
        }
        @keyframes ani-demo-spin {
            from { transform: rotate(0deg);}
            50%  { transform: rotate(180deg);}
            to   { transform: rotate(360deg);}
        }
        .ivu-spin-fix {
            background-color: rgba(55,55,55,0);
        }
        .load-text {
            font-size: 12px;
        }
        /* loading样式 end */
        // 数据趋势样式覆盖
        .keyAna {
            float: left;
            width: 100%;
            .keyCon {
                font-size: 14px;
                margin-top: 10px;
                padding:8px 15px;
                border:1px solid #ddd;
                span {
                    font-weight: bold;
                }
                .ivu-btn-group {
                    float: right;
                    margin-top: -4px;
                }
                .active {
                    color: #57a3f3;
                    background-color: #fff;
                    border-color: #57a3f3;
                }
            }
            // 明细数据
            .detailData {
                margin-top: 15px;
                border:1px solid #ddd;
                padding:15px;
            }
        }
    }
</style>
<template>
    <div class="con">
        <!-- <Spin fix v-show="loading">
            <Icon type="load-c" size=18 class="demo-spin-icon-load"></Icon>
            <div class="load-text">加载中...</div>
        </Spin> -->
        <!-- 明细数据统计 -->
        <div class="keyAna">
            <div class="keyCon">
                <span>明细数据统计</span>
                <Button-group>
                    <Button @click="expExcel">导出excel</Button>
                    <Button @click="table1" :class="[{active:btnActive === 1}]">表格1</Button>
                    <Button @click="table2" :class="[{active:btnActive === 2}]">表格2</Button>
                    <Button @click="table3" :class="[{active:btnActive === 3}]">表格3</Button>
                </Button-group>
            </div>
            <div class="detailData">
                <!-- 表格 -->
                <Table border :columns="this.tabHead" :data="this.tabData"></Table>
            </div>
        </div>
    </div>
</template>
<script>
    import { portExcel } from '../assets/js/Export2Excel.js';
    export default {
        data() {
            return {
                btnActive:1,//明细数据统计按钮点击状态
                tabHead:[],//初始化表格头部名称
                tabData:[],//初始化表格数据
                loading:false,//加载动画显示与隐藏
                // 明细数据(表格1)
                t1Header: [
                    {
                        title: '表格1',
                        key: 'addPeople1',
                        align:'center' 
                    },{
                        title: '表格1',
                        key: 'addPeople2',
                        align:'center'  
                    },{
                        title: '表格1',
                        key: 'addPeople3',
                        align:'center'  
                    },{
                        title: '表格1',
                        key: 'addPeople4',
                        align:'center'  
                    },{
                        title: '表格1',
                        key: 'addPeople5',
                        align:'center'  
                    },{
                        title: '表格1',
                        key: 'addPeople6',
                        align:'center'  
                    },{
                        title: '表格1',
                        key: 'addPeople7',
                        align:'center'  
                    },
                    {
                        title: '表格1',
                        key: 'addPeople8',
                        align:'center'  
                    },{
                        title: '表格1',
                        key: 'addPeople9',
                        align:'center'  
                    }
                ],
                detailData:[
                    {
                        addPeople1: '400',
                        addPeople2: '400',
                        addPeople3: '400',
                        addPeople4: '400',
                        addPeople5: '400',
                        addPeople6: '400',
                        addPeople7: '400',
                        addPeople8: '400',
                        addPeople9: '400'
                    },{
                        addPeople1: '400',
                        addPeople2: '400',
                        addPeople3: '400',
                        addPeople4: '400',
                        addPeople5: '400',
                        addPeople6: '400',
                        addPeople7: '400',
                        addPeople8: '400',
                        addPeople9: '400'
                    },{
                        addPeople1: '400',
                        addPeople2: '400',
                        addPeople3: '400',
                        addPeople4: '400',
                        addPeople5: '400',
                        addPeople6: '400',
                        addPeople7: '400',
                        addPeople8: '400',
                        addPeople9: '400'
                    },{
                        addPeople1: '400',
                        addPeople2: '400',
                        addPeople3: '400',
                        addPeople4: '400',
                        addPeople5: '400',
                        addPeople6: '400',
                        addPeople7: '400',
                        addPeople8: '400',
                        addPeople9: '400'
                    },{
                        addPeople1: '400',
                        addPeople2: '400',
                        addPeople3: '400',
                        addPeople4: '400',
                        addPeople5: '400',
                        addPeople6: '400',
                        addPeople7: '400',
                        addPeople8: '400',
                        addPeople9: '400'
                    }
                ],
                // 明细数据(表格2)
                t2Header: [
                    {
                        title: '表格2',
                        key: 'addPeople1',
                        align:'center' 
                    },{
                        title: '表格2',
                        key: 'addPeople2',
                        align:'center'  
                    },{
                        title: '表格2',
                        key: 'addPeople3',
                        align:'center'  
                    },{
                        title: '表格2',
                        key: 'addPeople4',
                        align:'center'  
                    },{
                        title: '表格2',
                        key: 'addPeople5',
                        align:'center'  
                    },{
                        title: '表格2',
                        key: 'addPeople6',
                        align:'center'  
                    },{
                        title: '表格2',
                        key: 'addPeople7',
                        align:'center'  
                    },
                    {
                        title: '表格2',
                        key: 'addPeople8',
                        align:'center'  
                    },{
                        title: '表格2',
                        key: 'addPeople9',
                        align:'center'  
                    }
                ],
                t2Data:[
                    {
                        addPeople1: '400',
                        addPeople2: '400',
                        addPeople3: '400',
                        addPeople4: '400',
                        addPeople5: '400',
                        addPeople6: '400',
                        addPeople7: '400',
                        addPeople8: '400',
                        addPeople9: '400',
                        addPeople10: '400',
                        addPeople11: '400',
                        addPeople12: '400'
                    },{
                        addPeople1: '400',
                        addPeople2: '400',
                        addPeople3: '400',
                        addPeople4: '400',
                        addPeople5: '400',
                        addPeople6: '400',
                        addPeople7: '400',
                        addPeople8: '400',
                        addPeople9: '400',
                        addPeople10: '400',
                        addPeople11: '400',
                        addPeople12: '400'
                    },{
                        addPeople1: '400',
                        addPeople2: '400',
                        addPeople3: '400',
                        addPeople4: '400',
                        addPeople5: '400',
                        addPeople6: '400',
                        addPeople7: '400',
                        addPeople8: '400',
                        addPeople9: '400',
                        addPeople10: '400',
                        addPeople11: '400',
                        addPeople12: '400'
                    },{
                        addPeople1: '400',
                        addPeople2: '400',
                        addPeople3: '400',
                        addPeople4: '400',
                        addPeople5: '400',
                        addPeople6: '400',
                        addPeople7: '400',
                        addPeople8: '400',
                        addPeople9: '400',
                        addPeople10: '400',
                        addPeople11: '400',
                        addPeople12: '400'
                    },{
                        addPeople1: '400',
                        addPeople2: '400',
                        addPeople3: '400',
                        addPeople4: '400',
                        addPeople5: '400',
                        addPeople6: '400',
                        addPeople7: '400',
                        addPeople8: '400',
                        addPeople9: '400',
                        addPeople10: '400',
                        addPeople11: '400',
                        addPeople12: '400'
                    }
                ],
                // 明细数据(表格3)
                t3Header: [
                    {
                        title: '表格3',
                        key: 'addPeople1',
                        align:'center' 
                    },{
                        title: '表格3',
                        key: 'addPeople2',
                        align:'center'  
                    },{
                        title: '表格3',
                        key: 'addPeople3',
                        align:'center'  
                    },{
                        title: '表格3',
                        key: 'addPeople4',
                        align:'center'  
                    },{
                        title: '表格3',
                        key: 'addPeople5',
                        align:'center'  
                    },{
                        title: '表格3',
                        key: 'addPeople6',
                        align:'center'  
                    },{
                        title: '表格3',
                        key: 'addPeople7',
                        align:'center'  
                    },
                    {
                        title: '表格3',
                        key: 'addPeople8',
                        align:'center'  
                    },{
                        title: '表格3',
                        key: 'addPeople7',
                        align:'center'  
                    }
                ],
                t3Data:[
                    {
                        addPeople1: '400',
                        addPeople2: '400',
                        addPeople3: '400',
                        addPeople4: '400',
                        addPeople5: '400',
                        addPeople6: '400',
                        addPeople7: '400',
                        addPeople8: '400',
                        addPeople9: '400',
                        addPeople10: '400',
                        addPeople11: '400'
                    },{
                        addPeople1: '400',
                        addPeople2: '400',
                        addPeople3: '400',
                        addPeople4: '400',
                        addPeople5: '400',
                        addPeople6: '400',
                        addPeople7: '400',
                        addPeople8: '400',
                        addPeople9: '400',
                        addPeople10: '400',
                        addPeople11: '400'
                    },{
                        addPeople1: '400',
                        addPeople2: '400',
                        addPeople3: '400',
                        addPeople4: '400',
                        addPeople5: '400',
                        addPeople6: '400',
                        addPeople7: '400',
                        addPeople8: '400',
                        addPeople9: '400',
                        addPeople10: '400',
                        addPeople11: '400'
                    },{
                        addPeople1: '400',
                        addPeople2: '400',
                        addPeople3: '400',
                        addPeople4: '400',
                        addPeople5: '400',
                        addPeople6: '400',
                        addPeople7: '400',
                        addPeople8: '400',
                        addPeople9: '400',
                        addPeople10: '400',
                        addPeople11: '400'
                    },{
                        addPeople1: '400',
                        addPeople2: '400',
                        addPeople3: '400',
                        addPeople4: '400',
                        addPeople5: '400',
                        addPeople6: '400',
                        addPeople7: '400',
                        addPeople8: '400',
                        addPeople9: '400',
                        addPeople10: '400',
                        addPeople11: '400'
                    }
                ]
            }
        },
        mounted(){
            let that = this;
            that.tabHead = that.t1Header;//明细数据默认为表格1数据
            that.tabData = that.detailData;
        },
        methods: {
            //调用导出excel表方法
            expExcel(){
                let that = this;
                switch(that.btnActive){
                    case 1:that.exportExcel(that.t1Header,that.detailData,'表格1');//表格1导出excel表
                    break;
                    case 2:that.exportExcel(that.t2Header,that.t2Data,'表格2');//表格2导出excel表
                    break;
                    case 3:that.exportExcel(that.t3Header,that.t3Data,'表格3');//表格3导出excel表
                    break;
                }
            },
            //导出excel方法
            exportExcel(tabHeaderName,tableData,excelName){
                let that = this,
                    title = [],
                    titleParam = [];   
                for(let i = 0;i < tabHeaderName.length;i++){
                    title.push(tabHeaderName[i].title);
                    titleParam.push(tabHeaderName[i].key);
                }
    　　　　　　require.ensure([], () => {
                    const tHeader = title,
                        filterVal = titleParam,
                        list = tableData,
                        data = that.fJson(filterVal, list),
                        fileName = excelName;
                        var strFileName = fileName.replace(/(.*\/)*([^.]+).*/ig,"$2");
                        strFileName = fileName;
        　　　　　　　　portExcel(tHeader, data, strFileName);
    　　　　　　})
    　　　　},
    　　　　fJson(filterVal, jsonData) {
    　　　　　　return jsonData.map(v => filterVal.map(j => v[j]))
    　　　　},
            // 表格1
            table1(){
                // debugger
                let that = this;
                that.btnActive = 1;
                that.tabHead = that.t1Header;
                that.tabData = that.detailData;
                console.log("表格1");
            },
            // 表格2
            table2(){
                let that = this;
                that.btnActive = 2;
                that.tabHead = that.t2Header;
                that.tabData = that.t2Data;
                console.log("表格2");
            },
            // 表格3
            table3(){
                let that = this;
                that.btnActive = 3;   
                that.tabHead = that.t3Header;
                that.tabData = that.t3Data;
                console.log("表格3");
            }
        }
    };
</script>