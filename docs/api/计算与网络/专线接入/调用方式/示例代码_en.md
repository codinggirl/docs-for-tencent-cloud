## 1. Download SDK code

- **Sample Code (PHP)**
	- [Go to github for PHP SDK >>](https://github.com/QcloudApi/qcloudapi-sdk-php)
	- [Click to download PHP SDK >>](https://mc.qcloudimg.com/static/archive/cd1857b4d9a9aeb0179e72a59f235c41/qcloudapi-sdk-php-master.zip)
- **Sample Code (JAVA)**
	- [Go to github for JAVA >>](https://github.com/QcloudApi/qcloudapi-sdk-java)
	- [Click to download JAVA SDK >>](https://mc.qcloudimg.com/static/archive/72dbc1a82ad8e18dead2e6dc07acd5d7/qcloudapi-sdk-java-master.zip)
- **Sample Code (Python)**
	- [Go to github for Python >>](https://github.com/QcloudApi/qcloudapi-sdk-python)
	- [Click to download Python SDK >>](https://mc.qcloudimg.com/static/archive/b61ee1ce734e7437530304152c20ee14/qcloudapi-sdk-python-master.zip)
- **Sample Code (.NET)**
	- [Go to github for .NET SDK >>](https://github.com/QcloudApi/qcloudapi-sdk-dotnet)
	- [Click to download .NET SDK >>](https://mc.qcloudimg.com/static/archive/b55098d83c78db530c53fb10f44c3fef/qcloudapi-sdk-dotnet-master.zip)

Replace `YOUR_SECRET_ID` and `YOUR_SECRET_KEY` in the sample code with the actual `SecretId` and `SecretKey`. 
The sample code is for reference only. Please use the code based on your actual needs.

## 2. Sample Codes in PHP

```
<?php


/***************In practice, the following parameters need to be changed based on the APIs called*********************************/
/***************The DescribeInstances is taken as an example to describe how to obtain the VM with the specified instanceId**********/

/*The URL of the DescribeInstances API is cvm.api.qcloud.com, which can be obtained from the "1. API Description" chapter*/
$HttpUrl="cvm.api.qcloud.com";

/*Unless otherwise specified, all APIs other than MultipartUploadVodFile support GET and POST methods*/
$HttpMethod="GET"; 

/*Most APIs are based on HTTPS protocol, except a small number of APIs such as MultipartUploadVodFile*/
$isHttps =true;

/*Your key is required. You can obtain SecretId and $SecretKey from https://console.cloud.tencent.com/capi*/
$secretKey='XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX';


/*The following five parameters are the common parameters of all APIs. For some APIs that are not region-specific (e.g. DescribeDeals), the Region parameter is not required*/
$COMMON_PARAMS = array(
        'Nonce'=> rand(),
        'Timestamp'=>time(NULL),
        'Action'=>'DescribeInstances',
        'SecretId'=> 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX',
        'Region' =>'gz',
);

/*The following two parameters are specific to DescribeInstances API, used to query specific VM list*/
$PRIVATE_PARAMS = array(
        'instanceIds.0'=> 'qcvm00001',
        'instanceIds.1'=> 'qcvm00002',
);


/***********************************************************************************/


CreateRequest($HttpUrl,$HttpMethod,$COMMON_PARAMS,$secretKey, $PRIVATE_PARAMS, $isHttps);


function CreateRequest($HttpUrl,$HttpMethod,$COMMON_PARAMS,$secretKey, $PRIVATE_PARAMS, $isHttps)
{
    $FullHttpUrl = $HttpUrl."/v2/index.php";
    
    /***************Sort the request parameters in ascending lexicographical order by their names (case-sensitive)*************/
    $ReqParaArray = array_merge($COMMON_PARAMS, $PRIVATE_PARAMS);
    ksort($ReqParaArray);
    
    /**********************************Generate original signature text**********************************
     * Join the request method, URI, and sorted request parameters into the following format to generate the original signature text. In this example, the original signature text is as follows: 
     * GETcvm.api.qcloud.com/v2/index.php?Action=DescribeInstances&Nonce=345122&Region=gz
     * &SecretId=AKIDz8krbsJ5yKBZQ	??1pn74WFkmLPx3gnPhESA&Timestamp=1408704141
     * &instanceIds.0=qcvm12345&instanceIds.1=qcvm56789
     * ****************************************************************************/
    $SigTxt = $HttpMethod.$FullHttpUrl."?";
    
    $isFirst = true;
    foreach ($ReqParaArray as $key => $value)
    {
        if (!$isFirst) 
        { 
            $SigTxt = $SigTxt."&";
        }
        $isFirst= false;
        
        /*In the construction of original signature text, any "_" in a parameter name should be replaced with "."
        if(strpos($key, '_'))
        {
            $key = str_replace('_', '.', $key);
        }
        
        $SigTxt=$SigTxt.$key."=".$value;
    }
    
    /*********************Generate a Signature based on the original signature string $SigTxt******************/
    $Signature = base64_encode(hash_hmac('sha1', $SigTxt, $secretKey, true));

    
    /***************Join the request strings together. The request parameters and Signature string need to be encoded with urlencode********************/
    $Req = "Signature=".urlencode($Signature);
    foreach ($ReqParaArray as $key => $value)
    {
        $Req=$Req."&".$key."=".urlencode($value);
    }
    
    /*********************************Send requests********************************/
    if($HttpMethod === 'GET')
    {
        if($isHttps === true)
        {
            $Req="https://".$FullHttpUrl."?".$Req;
        }
        else
        {
            $Req="http://".$FullHttpUrl."?".$Req;
        }
        
        $Rsp = file_get_contents($Req);
        
    }
    else
    {
        if($isHttps === true)
        {
        	$Rsp= SendPost("https://".$FullHttpUrl,$Req,$isHttps);
        }
        else
        {
        	$Rsp= SendPost("http://".$FullHttpUrl,$Req,$isHttps);
        }
    }
    
    var_export(json_decode($Rsp,true));
}

function SendPost($FullHttpUrl,$Req,$isHttps)
{
	
        $ch = curl_init();
        curl_setopt($ch, CURLOPT_POST, 1);
        curl_setopt($ch, CURLOPT_POSTFIELDS, $Req);
        
        curl_setopt($ch, CURLOPT_URL, $FullHttpUrl);
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
        if ($isHttps === true) {
            curl_setopt($ch, CURLOPT_SSL_VERIFYPEER,  false);
            curl_setopt($ch, CURLOPT_SSL_VERIFYHOST,  false);
        }
        
        $result = curl_exec($ch);
        
        return $result;
}
```
