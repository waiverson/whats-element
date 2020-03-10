> 定位一个网页DOM元素，一般会以 id,class,name 作为标识符，通过 `document.getElementById()`、`document.getElementByName()` 、 `document.querySelector()` 
原生API来定位获取指定元素。而针对一些无任何标识的节点，如 `<span>文本</sapn>` 是否有方法定位到它们呢？ 

## 使用方法
### 方式一、引入JavaScript文件

```javascript
<script src="whatsElement.js"></script>
 var whats = new whatsElement();
  document.addEventListener('mousedown', (event) => {
      const result = whats.getUniqueId(event.target)// getUniqueId()参数为空时，默认计算鼠标点击到的最后一个HTML元素。
      console.log(result) // {wid:'xxxx',type:'document.getElementById()'}
  })
```

### 方式二、npm包引用
安装依赖包
```
npm install whats-element --save
```

demo.js
```javascript
import whatsElement from 'whats-element';
 var whats = new whatsElement();
  const result = whats.getUniqueId();
```

## 运算结果
返回结果 
```javascript
result = {
  wid:"", // wid 为最终的DOM元素在网页中的唯一标识符
  type:"", // 结果为：document.getElementById(),document.getElementsByName(),document.querySelector()
  top:0, // 在文档中的位置 top
  left:0, // 在文档中的位置 left
  viewLeft:0, // 在视口的位置 left
  viewTop: 0, // 在视口的位置 top
  text: 'innerText'
}
```


## API
whatsElement 提供以下方法
* *`whatsElement.getTarget(queryString)`*  根据一个标识符获取一个HTML元素对象
* *`whatsElement.getUniqueId(HTMLElement)`*  输入一个HTML对象，计算出它的唯一标识符、定位方式
* *`whatsElement.draw(result)`*  根据 `whatsElement.getUniqueId(HTMLElement)`的结果在页面中渲染出结果信息。`pure` 版本不提供
* *`whatsElement.clean()`*  删除 `whatsElement.draw()` 在网页中绘制的提示框。 `pure` 版本不提供

## 更多
为了将代码极致压缩，提供pure版本whatsElement，该版本不包含UI，不到4kb
使用方法：

`import whatsElement from 'whats-element/pure'`

## 开发
* npm install
* npm install gulp -g
* gulp release // 打包至dist文件夹