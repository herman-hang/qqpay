## 安装
```php
composer require xiaohang/qqpay
```
## 代码演示

```php
$qqArr = [
    "mch_id"     => $qqPayInfo['qqpay_mchid'],//商户号
    "notify_url" => $request->domain().url("Palymat/test"),//异步通知回调地址
    "key"        => $qqPayInfo['qqpay_key'],//商户key
];
$param = [
    "out_trade_no"  =>  trade_no(),// 订单号         
    "trade_type"    =>  "NATIVE",// 固定值          
    "total_fee"     =>  $info['moneys'],// 单位为分            
    "body"          =>  $info['title'],//订单标题     
];
//实例化
$qq      = new \qqpay\QQPay($qqArr);
//下单操作
$unified = $qq->unifiedOrder($param);
if($unified["return_code"] == "SUCCESS" &&  $unified["result_code"] == "SUCCESS")
{
  //订单逻辑实现
}
```
