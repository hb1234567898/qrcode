# qrcode
解决导入qrcode无法直接在Ts中使用

#### 首先通过npm安装qrcode
npm install qrcode
#### 将qrcode导入ts声明
npm install @type/qrcode
#### 配置tsconfig.json
```
"compilerOptions": {
    ....
    **"allowSyntheticDefaultImports":true,**
```
#### 在需要使用qrcode的位置导入
```
import * as QRCode from 'qrcode'
imgUrl.value = await QRCode.toDataURL(result.data.codeUrl)
timer.value = setInterval(async () => {
    let result: PayResult = await reqQueryPayStatus($route.query.orderId as string)
    if (result.data) {
        dialogVisible.value = false
        ElMessage({
            type: 'success',
            message: '支付成功'
        })
        clearInterval(timer.value)
        getOrderInfo()
    }
}, 2000)
```
