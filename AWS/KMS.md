### 1. What is KMS？

AWS Key Management Service (AWS KMS) 是一项托管服务，可让您轻松创建和控制*客户主密钥* (CMK)，这是用于加密数据的加密密钥。

###  2. KMS can handle which problems？

+ 加密一些密码和API key 等等的敏感信息, 避免了在代码中使用明文造成一些安全事故

  

### 3. The approaches to use KMS

4 种

+ CLI
+ AWS 的控制台
+ 用clodfamation s定义资源代码的方式

### 4. You can do which action by using KMS (you should know at least 5 or more) ?

+ Define which IAM users and roles can manage keys
+ Define which IAM users and roles can use keys to encrypt and decrypt data
+ Define which IAM users and roles can manage keys
+ Choose to have AWS KMS automatically rotate your keys on an annual basis
+ Temporarily disable keys so they cannot be used by anyone
+ Re-enable disabled keys
+ Delete keys that you no longer use
+ Audit use of keys by inspecting logs in AWS CloudTrail

