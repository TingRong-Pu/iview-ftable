<template>
  <div class="demo">
    <p>stripe:
      <i-switch v-model="fTableOptions.stripe"></i-switch>
    </p>
    <p>border:
      <i-switch v-model="fTableOptions.border"></i-switch>
    </p>
    <p>showHeader:
      <i-switch v-model="fTableOptions.showHeader"></i-switch>
    </p>
    <p>loading:
      <i-switch v-model="fTableOptions.loading"></i-switch>
    </p>
    <p>disabledHover:
      <i-switch v-model="fTableOptions.disabledHover"></i-switch>
    </p>
    <p>highlightRow:
      <i-switch v-model="fTableOptions.highlightRow"></i-switch>
    </p>
    <p>
      <RadioGroup v-model="fTableOptions.size" type="button">
        <Radio label="small"></Radio>
        <Radio label="default"></Radio>
        <Radio label="large"></Radio>
      </RadioGroup>
    </p>

    <f-table :data="tabledata" v-bind="fTableOptions" @on-row-click="onRowClick" width="1000">
      <f-table-column type="expand" :width="100" align="center" fixed='left'>
        <template slot-scope="scope">
          展开
        </template>
      </f-table-column>
      <f-table-column type="selection" :width="100" align="center" v-if="fTableOptions.border"></f-table-column>
      <f-table-column title="Age" :width="200" prop="age" :filters="[{label: 'Greater than 25',value: 1}]" :filterMethod="()=>(true) "></f-table-column>
      <f-table-column title="Province" :width="200" prop="province"></f-table-column>
      <f-table-column title="City" :width="200" prop="city"></f-table-column>
      <f-table-column title="Postcode" :width="200" prop="zip"></f-table-column>
      <f-table-column title="Address" :width="200" prop="address"></f-table-column>
      <f-table-column title="Date" :width="200" prop="date"></f-table-column>
      <f-table-column title="Action" :width="300" fixed='right'>
        <template slot-scope="scope">
          <Button type="primary" @click="$Modal.info({
                    title: '提示',
                    content: `查看 ${scope.name} 的信息`
                })">查看</Button>
          <Button type="warning" @click="$Modal.warning({
                    title: '提示',
                    content: `点击编辑 ${scope.name} 的信息`
                })">编辑</Button>
          <Button type="error" @click="$Modal.error({
                    title: '警告',
                    content: `确定要删除用户： ${scope.name} ？`
                })">删除</Button>
        </template>
      </f-table-column>
    </f-table>
    <Page
    :total = 20
    :page-size = '10'>

    </Page>
  </div>
</template>

<script>
import fTable from "@/components/fTable/fTable";
import fTableColumn from "@/components/fTable/fTableColumn";
export default {
    components: {
        fTable,
        fTableColumn
    },
    data() {
        return {
            fTableOptions: {
                stripe: false,
                border: false,
                showHeader: true,
                loading: false,
                disabledHover: false,
                highlightRow: false,
                size: "default",
                noDataText: "暂无数据",
                noFilteredDataText: "暂无筛选结果"
            },
            tabledata: [
                {
                    name: "John Brown",
                    age: 18,
                    address: "New York No. 1 Lake Park",
                    province: "America",
                    city: "New York",
                    date: '2016-10-02',
                    zip: 100000
                },
                {
                    name: "Jim Green",
                    age: 24,
                    address: "Washington, D.C. No. 1 Lake Park",
                    province: "America",
                    city: "Washington, D.C.",
                    date: '2016-10-02',
                    zip: 100000
                },
                {
                    name: "Joe Black",
                    age: 30,
                    address: "Sydney No. 1 Lake Park",
                    province: "Australian",
                    city: "Sydney",
                    date: '2016-10-02',
                    zip: 100000
                },
                {
                    name: "Jon Snow",
                    age: 26,
                    address: "Ottawa No. 2 Lake Park",
                    province: "Canada",
                    city: "Ottawa",
                    date: '2016-10-02',
                    zip: 100000
                },
                {
                    name: "John Brown",
                    age: 18,
                    address: "New York No. 1 Lake Park",
                    province: "America",
                    city: "New York",
                    date: '2016-10-02',
                    zip: 100000
                },
                {
                    name: "Jim Green",
                    age: 24,
                    address: "Washington, D.C. No. 1 Lake Park",
                    province: "America",
                    city: "Washington, D.C.",
                    date: '2016-10-02',
                    zip: 100000
                },
                {
                    name: "Joe Black",
                    age: 30,
                    address: "Sydney No. 1 Lake Park",
                    province: "Australian",
                    city: "Sydney",
                    date: '2016-10-02',
                    zip: 100000
                },
                {
                    name: "Jon Snow",
                    age: 26,
                    address: "Ottawa No. 2 Lake Park",
                    province: "Canada",
                    city: "Ottawa",
                    date: '2016-10-02',
                    zip: 100000
                },{
                    name: "John Brown",
                    age: 18,
                    address: "New York No. 1 Lake Park",
                    province: "America",
                    city: "New York",
                    date: '2016-10-02',
                    zip: 100000
                },
                {
                    name: "Jim Green",
                    age: 24,
                    address: "Washington, D.C. No. 1 Lake Park",
                    province: "America",
                    city: "Washington, D.C.",
                    date: '2016-10-02',
                    zip: 100000
                },
                {
                    name: "Joe Black",
                    age: 30,
                    address: "Sydney No. 1 Lake Park",
                    province: "Australian",
                    city: "Sydney",
                    date: '2016-10-02',
                    zip: 100000
                },
                {
                    name: "Jon Snow",
                    age: 26,
                    address: "Ottawa No. 2 Lake Park",
                    province: "Canada",
                    city: "Ottawa",
                    date: '2016-10-02',
                    zip: 100000
                },{
                    name: "John Brown",
                    age: 18,
                    address: "New York No. 1 Lake Park",
                    province: "America",
                    city: "New York",
                    date: '2016-10-02',
                    zip: 100000
                },
                {
                    name: "Jim Green",
                    age: 24,
                    address: "Washington, D.C. No. 1 Lake Park",
                    province: "America",
                    city: "Washington, D.C.",
                    date: '2016-10-02',
                    zip: 100000
                },
                {
                    name: "Joe Black",
                    age: 30,
                    address: "Sydney No. 1 Lake Park",
                    province: "Australian",
                    city: "Sydney",
                    date: '2016-10-02',
                    zip: 100000
                },
                {
                    name: "Jon Snow",
                    age: 26,
                    address: "Ottawa No. 2 Lake Park",
                    province: "Canada",
                    city: "Ottawa",
                    date: '2016-10-02',
                    zip: 100000
                },{
                    name: "John Brown",
                    age: 18,
                    address: "New York No. 1 Lake Park",
                    province: "America",
                    city: "New York",
                    date: '2016-10-02',
                    zip: 100000
                },
                {
                    name: "Jim Green",
                    age: 24,
                    address: "Washington, D.C. No. 1 Lake Park",
                    province: "America",
                    city: "Washington, D.C.",
                    date: '2016-10-02',
                    zip: 100000
                },
                {
                    name: "Joe Black",
                    age: 30,
                    address: "Sydney No. 1 Lake Park",
                    province: "Australian",
                    city: "Sydney",
                    date: '2016-10-02',
                    zip: 100000
                },
                {
                    name: "Jon Snow",
                    age: 26,
                    address: "Ottawa No. 2 Lake Park",
                    province: "Canada",
                    city: "Ottawa",
                    date: '2016-10-02',
                    zip: 100000
                }
            ]
        };
    },
    methods: {
        onRowClick(args) {
            console.log(args);
        }
    }
};
</script>

<style>
.demo {
    padding: 20px;
}
.demo > p {
    margin-bottom: 10px;
}
</style>
