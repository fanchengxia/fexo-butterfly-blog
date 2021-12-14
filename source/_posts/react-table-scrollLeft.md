---
title: React控制Table横向滚动条的位置
abbrlink: 1
---
 ## 1.Table表格加上ref 和 scroll

```
	<Table
    ref={c => { this.finishedProductTable = c; }}
    bordered
    dataSource={[]}
    rowKey={(record, index) => index}
    pagination={false}
    columns={[]}
    scroll={{ x: true }}
  />
```
## 2. 找到表格的DOM节点，给ant-table-body赋值scrollLeft，offset可以自己计算出宽度，我这里暂时写死了500
```
  componentDidMount() {
    const offsetLeft = 500;
    this.locationTableScrollLeft(offsetLeft);
  }
  // 定位表格横向滚动条
  locationTableScrollLeft(offsetLeft) {
    const table = ReactDOM.findDOMNode(this.finishedProductTable);
    const tableBody = table.querySelector('.ant-table-body');
    tableBody.scrollLeft = offsetLeft;
  }
```
