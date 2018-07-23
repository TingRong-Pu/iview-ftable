## 背景

公司的项目需要用到iView，项目里的同事都觉得`Table`组件用起来不顺手，相对来说，element-ui 的`el-table`好理解。
所以就有了这个小组件(无奈脸)

## 注意事项

`fTable` 只是更改了 `columns` 的写法，其他的 `prop` 和 `Table` 一致
另外`Table` 的 `header`、`footer`、`loading` 3个 slot 没有实现

## 用法

```
    // import
    import fTable from "@/components/fTable/fTable";
    import fTableColumn from "@/components/fTable/fTableColumn";

    export default {
        components: {
            fTable,
            fTableColumn
        },
        data() {
            return {
                data: [{
                    name: "John Brown",
                    age: 18,
                    address: "New York No. 1 Lake Park",
                    date: "2016-10-03"
                }]
            };
        },
    };
```

```
    // template
    <f-table :data="data">
        <f-table-column type="expand" :width="60" align="center">
            <template slot-scope="scope">
                expand 的内容，可以是各种组件
            </template>
        </f-table-column>
        <f-table-column type="selection" :width="60" align="center"></f-table-column>
        <f-table-column title="名字" prop="name"></f-table-column>
        <f-table-column title="操作">
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
```
## demo

[here](https://codesandbox.io/s/km1ry8zrp7)
