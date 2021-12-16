---
title: 自定义的纵向滚动条自动定位
abbrlink: 1
---
## 自定义的纵向滚动条自动定位

本文的滚动条是自己写的，并非浏览器滚动条
### 注意事项：
**1. 滚动容器必须要有个相对定位的父元素**
**2.滚动容器和需要定位的锚点元素必须要加id属性**

以下代码可直接复制使用
```
import { Collapse, Select } from 'antd';
import React, { Component } from 'react';

const { Option } = Select;
const { Panel } = Collapse;
class index extends Component {
  state = {
    activeKey: '',
    contentList: [
      '你好',
      '非常荣幸认识你',
      '这是我写的例子',
      '欢迎观看',
      '有任何问题',
      '可以给我留言哦',
      '哈哈',
      '嘻嘻'
    ]
  }
  componentDidMount() {}

  handleChange = (value) => {
    const { contentList } = this.state;
    const index = contentList.indexOf(value)
    // 列表滚动到相应的位置
    let scrollElement = document.getElementById('father');    // 对应id的滚动容器
    let anchorElement = document.getElementById(index);  // 须要定位看到的锚点元素
    if (scrollElement && anchorElement) {
      scrollElement.scrollTo({ top: anchorElement.offsetTop, behavior: "smooth" });
    }
    // 给Collapse赋值activeKey
    this.setState({ activeKey: String(index) })
  }
  render() {
    const { contentList } = this.state;
    return (
      <div style={{ padding: 5 }}>
        <Select style={{ width: 300, marginBottom: 10 }}
          placeholder="请选择"
          onChange={this.handleChange}>
          {
            contentList && contentList.map(item => {
              return <Option value={item} key={item}>{item}</Option>
            })
          }
        </Select>
        {/* 滚动容器的父元素，必须要相对定位 */}
        <div style={{ position: 'relative' }}>
          {/* 滚动容器：要加id属性，自定义滚动条 */}
          <div style={{ width: 500, height: 200, overflow: 'auto' }} id="father">
            <Collapse
              onChange={(key) => {
                this.setState({ activeKey: key })
              }}
              activeKey={this.state.activeKey}
              destroyInactivePanel={true}
            >
              {
                contentList && contentList.map((item, i) => (
                  // 定位看到的锚点元素，要加id属性
                  <Panel header={"This is panel header " + (i + 1)} key={i} id={i}>
                    <p>{item}</p>
                  </Panel>
                ))
              }
            </Collapse>
          </div>
        </div>
      </div>
    )
  }
}

export default index;

```
