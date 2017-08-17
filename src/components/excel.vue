<template>
    <div class="excel-cmp">
        <button @click="columnSort">排序</button>

        <div class="excel-area" >
            <div class="table-head clearfix">
                <div class="first-col fl">
                    <table cellspacing="0" border="1">
                        <thead>
                        <tr>
                            <td>姓名</td>
                        </tr>
                        </thead>
                    </table>
                </div>
                <div class="other-col fl">
                    <div class="scorll">
                        <table cellspacing="0" border="1">
                            <thead>
                            <tr>
                                <td>年龄</td>
                                <td>职位</td>
                            </tr>
                            </thead>
                        </table>
                     </div>
                </div>
            </div>
            <div class="table-body clearfix" >
                <div class="first-col fl">
                    <table class="" cellspacing="0" border="1">
                        <tbody>
                        <tr v-for="(item,index) in excelList">
                            <td contenteditable="true" v-text="item.name" @input="inputHandler(index,$event,'name')"></td>
                        </tr>
                        </tbody>
                    </table>
                </div>
                <div class="other-col fl">
                    <div class="scorll" @scroll="rowScroll($event)">
                        <table cellspacing="0" border="1">
                            <tbody>
                            <tr v-for="(item,index) in excelList">
                                <td contenteditable="true" v-text="item.age" @input="inputHandler(index,$event,'age')"></td>
                                <td contenteditable="true" v-text="item.position" @input="inputHandler(index,$event,'position')"></td>
                            </tr>
                            </tbody>
                        </table>
                    </div>

                </div>
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
                    }
                });
            },
            rowScroll: function ($event) {
                this.tableScrollLeft = $event.target.scrollLeft;
                document.querySelectorAll('.table-head .scorll')[0].scrollLeft = this.tableScrollLeft;
            },
            colScroll: function () {
                console.log('4444');
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped type="text/css">
    .excel-cmp {
        .fl {
            float: left;
        }
        .clearfix:before {
            content: '';
            display: block;
            clear: both;
        }
        .clearfix {
            zoom:1;
        }
        .excel-area {
            width: 520px;
            height: 200px;
            margin-top: 30px;

            table {
                width: 100%;
                table-layout: fixed;
            }

            td {
                height: 30px;
            }
        }

        .table-head {
            height:37px;
            .other-col {
                height: 36px;
                overflow: hidden;
            }
        }

        .table-body {
            height: 200px;
            margin-top: -1px;
            overflow-y: scroll;
        }

        .first-col {
            width: 50px;
        }
        .other-col {
            width:450px;

            table {
                width: 600px;
            }

            .scorll {
                width: 450px;
                overflow-x: scroll;
            }
        }

    };




</style>
