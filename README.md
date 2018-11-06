ImageFile

image util to handle image file, canvas/image/blob/file translate

## use

```html
<input type="file" accept="image/*" onchange="fileChange(event)">
<script src="../dist/imageFile.umd.js"></script>
<script>
function fileChange(ev) {
    let file = ev.target.files[0];
    ImageFile.getImageFileData(file, { width: 300, height: 400, cover: false }).then(blob => {
        let img = ImageFile.blobToImage(blob);
        document.body.appendChild(img);
    });
}
</script>
```

## API

#### getImageFileData(file, option);

> 获取图片转换后的二进制数据

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| file | file type | 文件类型 |
| option | object | 配置项 |
|  | width | 宽度 |
|  | height | 高度 |
|  | cover | 是否覆盖整个区域，默认false |

```javascript
function fileChange(ev) {
    let file = ev.target.files[0];
    ImageFile.getImageFileData(file, { width: 300, height: 400, cover: true }).then(blob => {
        let img = ImageFile.blobToImage(blob);
        document.body.appendChild(img);
    })
}
```

#### fileToCanvas(file, option);

> 把文件转为canvas和image

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| file | file type | 文件类型 |
| option | object | 配置项 |
|  | width | 宽度 |
|  | height | 高度 |
|  | cover | 是否覆盖整个区域，默认false |

```javascript
ImageFile.fileToCanvas(file, { width: 400, height: 400 }).then(({ canvas, image }) => {
    document.body.appendChild(canvas);
})
```

#### fileToImage(file);

> 文件转为图片

```
ImageFile.fileToImage(file).then(img => {
    document.body.appendChild(img);
})
```

#### imageToCanvas(img);

> image to canvas

```javascript
let canvas = ImageFile.imageToCanvas(img);
```

#### imageToBase64(img);

> image to base64

```javascript
let base64 = ImageFile.imageToBase64(img);
```

#### rotate(canvas, image, degree);

> 旋转图片，可以把旋转后的图片转二进制上传

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| canvas | canvas | 需要绘制的canvs |
| image | img | img元素 |
| degree  | int | 角度 |
