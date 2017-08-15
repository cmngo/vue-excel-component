<template>
    <div class="excel">
        <button @click="columnSort">排序</button>
        <button @click="freezeRow">冻结首行</button>
        <button @click="freezeCol">冻结首列</button>

        <!--<div class="excel-area" v-show="false">-->
            <!--<table class=".table" cellspacing="0" border="1">-->
                <!--<div class="fixed-head">-->
                    <!--<thead>-->
                        <!--<tr>-->
                            <!--<td>姓名</td>-->
                            <!--<td>年龄</td>-->
                            <!--<td>职位</td>-->
                        <!--</tr>-->
                    <!--</thead>-->
                <!--</div>-->
                <!--<tbody>-->
                    <!--<tr v-for="(item,index) in excelList">-->
                        <!--<td contenteditable="true" v-text="item.name" @input="inputHandler(index,$event,'name')"></td>-->
                        <!--<td contenteditable="true" v-text="item.age" @input="inputHandler(index,$event,'age')"></td>-->
                        <!--<td contenteditable="true" v-text="item.position" @input="inputHandler(index,$event,'position')"></td>-->
                    <!--</tr>-->
                <!--</tbody>-->
            <!--</table>-->
        <!--</div>-->

        <div class="excel-area" >
            <div class="table-head">
                <table cellspacing="0" border="1">
                    <colgroup>
                        <col />
                        <col />
                        <col />
                    </colgroup>
                    <thead>
                    <tr>
                        <td>姓名</td>
                        <td>年龄</td>
                        <td>职位</td>
                    </tr>
                    </thead>
                </table>
            </div>
            <div class="table-body" >
                <table cellspacing="0" border="1">
                    <tbody>
                    <tr v-for="(item,index) in excelList">
                        <td contenteditable="true" v-text="item.name" @input="inputHandler(index,$event,'name')"></td>
                        <td contenteditable="true" v-text="item.age" @input="inputHandler(index,$event,'age')"></td>
                        <td contenteditable="true" v-text="item.position" @input="inputHandler(index,$event,'position')"></td>
                    </tr>
                    </tbody>
                </table>
            </div>
        </div>


        <div style="width: 800px;" class="test">
            <div class="table-head">
                <table>
                    <colgroup>
                        <col style="width: 80px;" />
                        <col />
                    </colgroup>
                    <thead>
                    <tr><th>序号</th><th>内容</th></tr>
                    </thead>
                </table>
            </div>
            <div class="table-body">
                <table>
                    <colgroup><col style="width: 80px;" /><col /></colgroup>
                    <tbody>
                    <tr><td>1</td><td>我只是用来测试的</td></tr>
                    <tr><td>2</td><td>我只是用来测试的</td></tr>
                    <tr><td>3</td><td>我只是用来测试的</td></tr>
                    <tr><td>4</td><td>我只是用来测试的</td></tr>
                    <tr><td>5</td><td>我只是用来测试的</td></tr>
                    <tr><td>6</td><td>我只是用来测试的</td></tr>
                    <tr><td>7</td><td>我只是用来测试的</td></tr>
                    <tr><td>8</td><td>我只是用来测试的</td></tr>
                    <tr><td>9</td><td>我只是用来测试的</td></tr>
                    <tr><td>10</td><td>我只是用来测试的</td></tr>
                    <tr><td>11</td><td>我只是用来测试的</td></tr>
                    <tr><td>12</td><td>我只是用来测试的</td></tr>
                    <tr><td>13</td><td>我只是用来测试的</td></tr>
                    <tr><td>14</td><td>我只是用来测试的</td></tr>
                    <tr><td>15</td><td>我只是用来测试的</td></tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'excel',
        data:function () {
            return {
                sortName: 'age',
                sortTyle: 'stl',
                excelList: [
                    {
                        name: 'a',
                        age: 1,
                        position: '阿阿阿'
                    },
                    {
                        name: 'h',
                        age: 8,
                        position: '哈哈哈'
                    },
                    {
                        name: 'f',
                        age: 6,
                        position: '发发发'
                    },
                    {
                        name: 'c',
                        age: 3,
                        position: '呲呲呲'
                    },
                    {
                        name: 'g',
                        age: 7,
                        position: '哥哥哥'
                    },
                    {
                        name: 'e',
                        age: 5,
                        position: '额额额'
                    },
                    {
                        name: 'a',
                        age: 1,
                        position: '阿阿阿'
                    },
                    {
                        name: 'h',
                        age: 8,
                        position: '哈哈哈'
                    },
                    {
                        name: 'f',
                        age: 6,
                        position: '发发发'
                    },
                    {
                        name: 'c',
                        age: 3,
                        position: '呲呲呲'
                    },
                    {
                        name: 'g',
                        age: 7,
                        position: '哥哥哥'
                    },
                    {
                        name: 'e',
                        age: 5,
                        position: '额额额'
                    },
                ]
            }
        },
        mounted: function () {
        },
        methods: {
            inputHandler: function (index,$event,type) {
                console.log($event);
                this.excelList[index][type] = $event.target.innerText;
            },
            columnSort: function () {
                var type = this.sortName;
                var excelData = this.excelList;

                this.excelList = excelData.sort(function (a,b) {
                    // 需要考虑不是数字的情况
                    var aInput = a[type];
                    var bInput = b[type];
                    if(!isNaN(+aInput) && !isNaN(+bInput) ){
                        return aInput - bInput;
                    }else {
                        return aInput.localeCompare(bInput);
//                        console.log('888888');
                    }
                });
            },
            freezeRow: function () {

            },
            freezeCol: function () {

            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped type="text/css">
    body {
        .excel-area {
            width: 700px;
            /*height:300px;*/
            margin-top: 30px;
            overflow-x: scroll;

            table {
                width: 900px;
                table-layout: fixed;

            }
        }

        /*.table {*/
            /*table-layout:fixed;*/
            /*position: relative;*/
            /*width: 900px;*/
            /*height: 500px;*/
            /*td {*/
                /*height: 30px;*/
                /*!*width: 33%;*!*/
            /*}*/
            /*thead {*/
                /*tr {*/
                    /*width: 100%;*/
                    /*position: fixed;*/
                    /*left:0;*/
                    /*right:0;*/
                /*}*/

                /*tr {*/
                    /*overflow: hidden;*/
                    /*height: 30px;*/
                /*}*/
            /*}*/
            /*tbody {*/
                /*tr {*/
                    /*td:first-child {*/

                        /*color: red;*/
                    /*}*/
                /*}*/
            /*}*/
        /*}*/

    .table-head {
        padding-right: 17px;
    }

    .table-body {
        overflow-y: scroll;

        height: 200px;
    }

    colgroup {
        col {
        }
    }
    };
    button {
        /*margin-bottom: 50px;*/
    }
    .fixed-head {
        height: 30px;
        overflow: hidden;
    }

    .test {
        .table-head{padding-right:17px;background-color:#999;color:#000;}
        .table-body{width:100%; height:300px;overflow-y:scroll;}
        .table-head table,.table-body table{width:100%;}
        .table-body table tr:nth-child(2n+1){background-color:#f2f2f2;}
    }



</style>
