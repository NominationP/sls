# 外部数据源API {#reference_psc_s44_12b .reference}

## 创建External Store {#section_iq3_nk5_12b .section}

**请求语法**

```
POST /externalstores HTTP/1.1
'x-log-bodyrawsize': '0',
'Content-Type': 'application/json', 
'Content-Length': <ContentLength>, 
'Content-MD5': <Md5>, 
'x-log-apiversion': '0.6.0', 
'x-log-signaturemethod': 'hmac-sha1', 
'Host': <Project Endpoint> 
'Date': <GMT Date>, 
'Authorization': <AuthorizationString> 
'{"externalStoreName": "<ExternalStoreName>", 
  "storeType": "rds-vpc", 
  "parameter": {
               "vpc-id": "<vpc-id>", 
               "instance-id": "<instance-id>", 
               "host": "<host>", 
               "port": "<port>", 
               "username": "<username>", 
               "password": "<password>", 
               "db": "<db>", 
               "table": "<table>", 
               "region": "region>"
               }
}'
```

**请求参数**

|属性名称|类型|是否必须|描述|
|:---|:-|:---|:-|
|ExternalStoreName|string|是|External Store名称，Project下和Logstore名称不冲突，保持唯一。|
|vpc-id|string|否|RDS所在VPC ID。|
|instance-id|string|否|RDS所在instance。vpc-id和instance-id可以同时为空，表示不在VPC环境中，能够直接访问。|
|host|string|否|RDS所在host，如果vpc和instance留空，那么host必须填写。|
|port|string|是|RDS的端口。|
|username|string|是|用户名。|
|password|string|是|密码。|
|db|string|是|数据库名称。|
|table|string|是|表名。|
|region|string|是|RDS所在region，目前仅支持cn-qingdao、cn-beijing、cn-hangzhou。|

**请求头**

CreateExternalStore 接口无特有请求头，关于 Log Service API 的公共请求头请参考 公共请求头。

**创建样例**

```
POST /externalstores HTTP/1.1
'x-log-bodyrawsize': '0',
'Content-Type': 'application/json', 
'Content-Length': '307', 
'Content-MD5': '7C1D14659C0BBBA7C7BFF9E5A1A46705', 
'x-log-apiversion': '0.6.0', 
'x-log-signaturemethod': 'hmac-sha1', 
'Host': 'ali-yunlei-chengdu.cn-chengdu.log.aliyuncs.com', 
'Date': 'Thu, 19 Apr 2018 02:15:41 GMT', 
'Authorization': 'LOG LTAIDbs0FWzQtYAl:E2CeD7yIRXsZjkb+nUDoJFbGM1E='}
'{"externalStoreName": "rds_store", 
  "storeType": "rds-vpc", 
  "parameter": {
               "vpc-id": "vpc-m5eq4irc1pucpk85frr5j", 
               "instance-id": "i-m5eeo2whsnfg4kzq54ah", 
               "host": "47.104.78.128", 
               "port": "3306", 
               "username": "root", 
               "password": "sfdsfldsfksflsdfs", 
               "db": "meta", 
               "table": "join_meta", 
               "region": "cn-qingdao"
               }}'
```

## 修改External Store {#section_ozr_rn5_12b .section}

**请求语法**

```
PUT /externalstores/<ExternalStoreName> HTTP/1.1
'x-log-bodyrawsize': '0',
'Content-Type': 'application/json', 
'Content-Length': <ContentLength>, 
'Content-MD5': <Md5>, 
'x-log-apiversion': '0.6.0', 
'x-log-signaturemethod': 'hmac-sha1', 
'Host': <Project Endpoint> 
'Date': <GMT Date>, 
'Authorization': <AuthorizationString> 
'{"externalStoreName": "<ExternalStoreName>", 
  "storeType": "rds-vpc", 
  "parameter": {
               "vpc-id": "<vpc-id>", 
               "instance-id": "<instance-id>", 
               "host": "<host>", 
               "port": "<port>", 
               "username": "<username>", 
               "password": "<password>", 
               "db": "<db>", 
               "table": "<table>", 
               "region": "region>"
               }
}'
```

**请求参数**

|属性名称|类型|是否必须|描述|
|:---|:-|:---|:-|
|ExternalStoreName|string|是|External Store名称，Project下和Logstore名称不冲突，保持唯一。|
|vpc-id|string|否|RDS所在VPC ID。|
|intance-id|string|否|RDS所在instance。vpc-id和instance-id可以同时为空，表示不在VPC环境中，能够直接访问。|
|host|string|否|RDS所在host，如果VPC和instance留空，那么host必须填写。|
|port|string|是|RDS的端口。|
|username|string|是|用户名。|
|password|string|是|密码。|
|db|string|是|数据库名称。|
|table|string|是|表名。|
|region|string|是|RDS所在Region，目前仅支持cn-qingdao、cn-beijing、cn-hangzhou。|

**修改样例**

```
PUT http://ali-yunlei-chengdu.cn-chengdu.log.aliyuncs.com:80/externalstores/rds_store  HTTP/1.1
'x-log-bodyrawsize': '0',
'Content-Type': 'application/json', 
'Content-Length': '307', 
'Content-MD5': '7C1D14659C0BBBA7C7BFF9E5A1A46705', 
'x-log-apiversion': '0.6.0', 
'x-log-signaturemethod': 'hmac-sha1', 
'Host': 'ali-yunlei-chengdu.cn-chengdu.log.aliyuncs.com', 
'Date': 'Thu, 19 Apr 2018 02:15:41 GMT', 
'Authorization': 'LOG LTAIDbs0FWzQtYAl:E2CeD7yIRXsZjkb+nUDoJFbGM1E='}
'{"externalStoreName": "rds_store", 
  "storeType": "rds-vpc", 
  "parameter": {
               "vpc-id": "vpc-m5eq4irc1pucpk85frr5j", 
               "instance-id": "i-m5eeo2whsnfg4kzq54ah", 
               "host": "47.104.78.128", 
               "port": "3306", 
               "username": "root", 
               "password": "sfdsfldsfksflsdfs", 
               "db": "meta", 
               "table": "join_meta", 
               "region": "cn-qingdao"
               }}'
```

## 列出所有的External Store {#section_ivh_vn5_12b .section}

**请求语法**

```
GET /externalstores?externalStoreName=<external_store_name_prefix>&offset=<offset>&lines=<lines>
'Content-Length': '0', 
'x-log-bodyrawsize': '0', 
'x-log-apiversion': '0.6.0', 
'x-log-signaturemethod': 
'hmac-sha1', 
'Host': '<endpoint>',
'Date': 'Thu, 19 Apr 2018 03:03:16 GMT', 
'Authorization': 'LOG LTAIDbs0FWzQtYAl:iZJXISaDEju6TJpPDf+CLOiserk='}
```

**请求参数**

|属性名称|类型|是否必须|描述|
|:---|:-|:---|:-|
|externalStoreName|string|否|用户过滤出包含该字符串的External Store。|
|offset|integer|否|表示从offset开始获取。|
|lines|integer|否|表示获取lines个External Store。|

**样例**

```
GET http://ali-yunlei-chengdu.cn-chengdu.log.aliyuncs.com:80/externalstores?externalStoreName=&offset=0&lines=10
'Content-Length': '0', 
'x-log-bodyrawsize': '0', 
'x-log-apiversion': '0.6.0', 
'x-log-signaturemethod': 
'hmac-sha1', 
'Host': 'ali-yunlei-chengdu.cn-chengdu.log.aliyuncs.com',
'Date': 'Thu, 19 Apr 2018 03:03:16 GMT', 
'Authorization': 'LOG LTAIDbs0FWzQtYAl:iZJXISaDEju6TJpPDf+CLOiserk='}
```

**响应**

```
{'count': 3, 'externalstores': ['ecs_store', 'rds_store', 'ecs_store1'], 'total': 3}
```

## 获取External Store详情 {#section_qxr_yn5_12b .section}

```
http://ali-yunlei-chengdu.cn-chengdu.log.aliyuncs.com:80/externalstores/<external_store_name> 
'Content-Length': '0', 
'x-log-bodyrawsize': '0', 
'x-log-apiversion': '0.6.0', 
'x-log-signaturemethod': 'hmac-sha1', 
'Host': 'ali-yunlei-chengdu.cn-chengdu.log.aliyuncs.com', 
'Date': 'Thu, 19 Apr 2018 03:26:49 GMT', 
'Authorization': 'LOG LTAIDbs0FWzQtYAl:a16W7ej3c0RqdQn3Pvnq5aHWEOk='
```

**请求参数**

|属性名称|类型|是否必须|描述|
|:---|:-|:---|:-|
|external\_store\_name|string|是|用于获取External Store名称|

**样例**

```
http://ali-yunlei-chengdu.cn-chengdu.log.aliyuncs.com:80/externalstores/rds_store
'Content-Length': '0', 
'x-log-bodyrawsize': '0', 
'x-log-apiversion': '0.6.0', 
'x-log-signaturemethod': 'hmac-sha1', 
'Host': 'ali-yunlei-chengdu.cn-chengdu.log.aliyuncs.com', 
'Date': 'Thu, 19 Apr 2018 03:26:49 GMT', 
'Authorization': 'LOG LTAIDbs0FWzQtYAl:a16W7ej3c0RqdQn3Pvnq5aHWEOk='
```

**响应**

```
{
  'storeType': 'rds-vpc', 
  'parameter': {
               'region': 'cn-qingdao', 
               'vpc-id': 'vpc-m5eq4irc1pucpk85frr5j', 
               'instance-id': 'i-m5eeo2whsnfg4kzq54ah', 
               'host': '47.104.78.128', 
               'port': '3306', 
               'username': 'root', 
               'db': 'meta', 
               'table': 'join_meta'
               }
}
```

## 删除External Store {#section_nq2_j45_12b .section}

```
DELETE /externalstores/<external_store_name>
'Content-Length': '0',
'x-log-bodyrawsize': '0', 
'x-log-apiversion': '0.6.0', 
'x-log-signaturemethod': 'hmac-sha1', 
'Host': 'ali-yunlei-chengdu.cn-chengdu.log.aliyuncs.com', 
'Date': 'Thu, 19 Apr 2018 03:32:49 GMT', 
'Authorization': 'LOG LTAIDbs0FWzQtYAl:7CtslFnYg+WEIt56Bsf2Xy4faw8='
```

**请求参数**

|属性名称|类型|是否必须|描述|
|:---|:-|:---|:-|
|external\_store\_name|string|是|要删除的External Store名称。|

**样例**

```
 DELETE http://ali-yunlei-chengdu.cn-chengdu.log.aliyuncs.com:80/externalstores/rds_store
'Content-Length': '0',
'x-log-bodyrawsize': '0', 
'x-log-apiversion': '0.6.0', 
'x-log-signaturemethod': 'hmac-sha1', 
'Host': 'ali-yunlei-chengdu.cn-chengdu.log.aliyuncs.com', 
'Date': 'Thu, 19 Apr 2018 03:32:49 GMT', 
'Authorization': 'LOG LTAIDbs0FWzQtYAl:7CtslFnYg+WEIt56Bsf2Xy4faw8='
```

