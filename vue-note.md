## vue技巧分享


##### 数组索引更新
```javascript
this.dataList[index] = newValue
this.dataList.__ob__.dep.notify()
```
