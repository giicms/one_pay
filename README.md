## Installation

The preferred way to install this extension is through composer.

Either run

composer require "giicms/one_pay" "dev-master"
or add

"giicms/one_pay": "dev-master"
to the require section of your application's composer.json file.

$onepay = new Onepay(); 

// cài đặt thông số bắt buộc 
```
$onepay->setupMerchant($merchant, $access, $secure); 
```
// $order_info bat buoc viet tieng Viet, khong dau, va it hon 30 ky tu, nen dung order_id. 
// Noi dia
```
$refer = $onepay->build_link($order_id, $total_amount, $order_info, $url_return); 
```
// Quoc te
```
$refer = $onepay->build_link_int($order_id, $total_amount, $order_info, $url_return); 
```

// Chuyển trang


```
$onepay = new Onepay(); 
// cài đặt thông số bắt buộc 
$onepay->setupMerchant($merchant, $access, $secure); 
$hashValidated = $onepay->validate($_GET); 
//Lấy thông tin giao dịch 
// Define Variables 
// ---------------- 
// Extract the available receipt fields from the VPC Response 
// If not present then let the value be equal to 'No Value Returned' 
// Standard Receipt Data 
$amount = $onepay->null2unknown ( $_GET ["vpc_Amount"] ); 
$locale = $onepay->null2unknown ( $_GET ["vpc_Locale"] ); 
$batchNo = $onepay->null2unknown ( $_GET ["vpc_BatchNo"] ); 
$command = $onepay->null2unknown ( $_GET ["vpc_Command"] ); 
$message = $onepay->null2unknown ( $_GET ["vpc_Message"] ); 
$version = $onepay->null2unknown ( $_GET ["vpc_Version"] ); 
$cardType = $onepay->null2unknown ( $_GET ["vpc_Card"] ); 
$orderInfo = $onepay->null2unknown ( $_GET ["vpc_OrderInfo"] ); 
$receiptNo = $onepay->null2unknown ( $_GET ["vpc_ReceiptNo"] ); 
$merchantID = $onepay->null2unknown ( $_GET ["vpc_Merchant"] ); 
$authorizeID = $onepay->null2unknown ( $_GET ["vpc_AuthorizeId"] ); 
$merchTxnRef = $onepay->null2unknown ( $_GET ["vpc_MerchTxnRef"] ); 
$transactionNo = $onepay->null2unknown ( $_GET ["vpc_TransactionNo"] ); 
$acqResponseCode = $onepay->null2unknown ( $_GET ["vpc_AcqResponseCode"] ); 
$txnResponseCode = $onepay->null2unknown ( $_GET ["vpc_TxnResponseCode"] ); 
$transStatus = ""; 
if($hashValidated=="CORRECT" && $txnResponseCode=="0"){ 
    $transStatus = 2; 
}elseif ($txnResponseCode!="0"){ 
    $transStatus = 0; 
}elseif ($hashValidated=="INVALID HASH"){ 
    $transStatus = 3; 
} 
// code xu ly cua ban
```
