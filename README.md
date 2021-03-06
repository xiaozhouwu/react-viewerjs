# react-viewerjs

[View README in English](README-en.md)

图片预览;对[viewerjs](https://github.com/fengyuanchen/viewerjs)库的react封装


## 安装

npm i react-viewerjs

## API

### RViewer组件配置参数

| 参数        | 说明     | 类型           | 默认值  | 是否必须 |
| --------- | ------ | ------------ | ---- | ---- |
| imageUrls | 单张图片预览地址（使用字符串）或者多张图片预览地址集合（使用数组） | string\|array | undefined    | 是 |
| options | 预览配置参见（[viewerjs options](https://github.com/fengyuanchen/viewerjs#options)） | object | undefined    | 否 |

### RViewerTrigger组件说明

该组件只有一个元素，用于触发图片预览

| 参数        | 说明     | 类型           | 默认值 | 是否必须 |
| --------- | ------ | ------------ | ---- | ---- |
| index | 预览触发显示索引为index图片，默认为0，显示第一张 | number | 0    | 否 |

### 例子

- #### 基础
````jsx
import React from "react"
import { RViewer, RViewerTrigger } from '../react-viewerjs'
const OneImagePreview = () => {
  let sourceUrl = "./imgs/1.jpg"
  let options={
    toolbar: {//单张图片预览不要pre和next底部按钮，隐藏它
      prev: false,
      next: false
    }
  }
  return (
    <RViewer options={options} imageUrls={sourceUrl}>
      <RViewerTrigger>
        <button>one image preview</button>
      </RViewerTrigger>
    </RViewer>
  )
}
const MultiImagePreview = () => {
  let sourceUrl = ["./imgs/1.jpg","./imgs/2.jpg","./imgs/3.jpg","./imgs/4.jpg","./imgs/5.jpg"]
  return (
    <RViewer imageUrls={sourceUrl}>
      <RViewerTrigger>
        <button>Multiple images preview</button>
      </RViewerTrigger>
    </RViewer>
  )
}
const BaseDemoComponent = () => {
  
  return (
    <div>
      <OneImagePreview />
      <MultiImagePreview />
    </div>
  )
};
ReactDOM.render(<BaseDemoComponent />, document.getElementById('root'));
````
https://xiabingwu.github.io/react-viewerjs/#/ 

- #### 列表
````jsx
import React from "react"
import { RViewer, RViewerTrigger } from '../react-viewerjs'
const ListDemoComponent = () => {
  let sourceImageUrls = [
    "./imgs/1.jpg",
    "./imgs/2.jpg",
    "./imgs/3.jpg",
    "./imgs/4.jpg",
    "./imgs/5.jpg"
  ]
  let thumbImageUrls = sourceImageUrls//小图和原图一样，只是为了演示方便
  return (
    <RViewer imageUrls={sourceImageUrls}>
      <ul>
        {thumbImageUrls.map((pic, index) => {
          return (
            <li  key={index} style={{marginBottom:"20PX"}}>
              <span>image {index+1}</span>
              {/*这里需要设置index值，告知触发图片预览该显示哪张图片*/}
              <RViewerTrigger index={index}>
                <img src={pic} style={{width:"50px",verticalAlign:"middle"}}  />
              </RViewerTrigger>
            </li>
          )
        })
        }
      </ul>
    </RViewer>
  )
};
ReactDOM.render(<ListDemoComponent />, document.getElementById('root'));
````
https://xiabingwu.github.io/react-viewerjs/#/list
