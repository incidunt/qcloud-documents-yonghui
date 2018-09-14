## Put Replication

### ��������

Put Bucket Replication ������������汾����Ĵ洢Ͱ��� replication ���á�����洢Ͱ�Ѿ�ӵ�� replication ���ã���ô��������滻�������á�

### ϸ�ڷ���


1. ʹ�øýӿڴ洢Ͱ�����Ѿ�����汾�����汾������ϸ��μ�[Put Bucket Versioning](/document/product/436/8591 "Put Bucket Versioning")

### Response

#### Special Errors

|������|����|HTTP״̬��|
|:--|:--|:--|
|MalformedXML|XML��ʽ���Ϸ�,���restful api�ĵ���ϸ�ȶ� |400 Bad Request|
|MultiBucketNotSupport|��������ֻ����һ��Ŀ��bucket|400 Bad Request|
|NotSupportedStorageClass|ָ���Ĵ洢���Ͳ��Ϸ�|400 Bad Request|
|InvalidBucketState|bucket״̬����������ͻ�������汾������������Ƶĳ�ͻ|409 Conflict|
|InvalidBucketName|Bucket���Ʋ��Ϸ�|400 Bad Request|

��ע������Ĵ���ԭ��ɲο����ص�message�����Ų顣
��ȡ�������COS�Ĵ��������Ϣ�����߲�Ʒ���еĴ����б���鿴[������](/document/product/436/7730)

## Get Replication

### ��������

Get Bucket Replication �ӿ�����ʵ�ֶ�ȡ�洢Ͱ���û���������������Ϣ��

### ϸ�ڷ���

### Response

#### Special Errors

|������|����|HTTP״̬��|
|:--|:--|:--|
|NoSuchBucket|�����ʵ�Bucket������|404 Not Found|

��ע������Ĵ���ԭ��ɲο����ص�message�����Ų顣
��ȡ�������COS�Ĵ��������Ϣ�����߲�Ʒ���еĴ����б���鿴[������](/document/product/436/7730)

## Put Bucket Lifecycle

### ��������

COS ֧���û��������������õķ�ʽ������ Bucket �� Object ���������ڡ������������ð���һ��������Ӧ����һ��������Ĺ��� (����ÿ������Ϊ COS ����һ������)��

### ϸ�ڷ���
Put Bucket Lifecycle ����Ϊ Bucket ����һ���µ������������á������ Bucket �������������ڣ�ʹ�øýӿڴ����µ����õ�ͬʱ��Ḳ��ԭ�е����á�

### Response

#### Special Errors

|������|����|HTTP״̬��|
|:--|:--|:--|
|NoSuchBucket|�����ʵ�Bucket������|404 Not Found|
|MalformedXML|XML��ʽ���Ϸ�,���restful api�ĵ���ϸ�ȶ� |400 Bad Request|
|InvalidRequest|���󲻺Ϸ������������������ʾ"Conflict lifecycle rule"����ô��ʾxml�����еĶ���rule���໥��ͻ�Ĳ��֡�|400 Bad Reques|
|InvalidArgument|����������Ϸ�, ���������������ʾ"Rule ID must be unique. Found same ID for more than one rule", ��ô��ʾ�ж��Rule��id�ֶ���ͬ��|400 Bad Reques|


��ע������Ĵ���ԭ��ɲο����ص�message�����Ų顣
��ȡ�������COS�Ĵ��������Ϣ�����߲�Ʒ���еĴ����б���鿴[������](/document/product/436/7730)

## Get Bucket Lifecycle

### ��������

Get Bucket Lifecycle ������ѯ Bucket �������������á�

### ϸ�ڷ���

### Response

#### Special Errors

|������|����|HTTP״̬��|
|:--|:--|:--|
|NoSuchBucket|�����ʵ�Bucket������|404 Not Found|
|NoSuchLifecycleConfiguration|�����������ò����ڡ�|404 Not Found|

## Post Object

### ��������

Post Objectʹ��HTML���ϴ��ļ���ָ��bucket��

### ϸ�ڷ���

### Response

#### Special Errors

|������|����|HTTP״̬��|
|:--|:--|:--|
|MalformedPOSTRequest|��POST�����Body���ݲ��Ϸ�|400 Bad Request|
|InvalidArgument|����������Ϸ�|404 Not Found|
