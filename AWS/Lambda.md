1. 创建fuction:

   ```
   aws lambda create-function --function-name my-function-mh-cli \
   --zip-file fileb://function.zip --handler index.handler --runtime nodejs12.x \
   --role arn:aws:iam::xxxxxx:role/lambda-s3-role-mh
   ```



2. invoke function

   ```shell
   aws lambda invoke --function-name my-function-mh-cli out --log-type Tail \
   --query 'LogResult' --output text |  base64 -D
   ```


3.

4. Access s3 bucket and read file from s3 bucket

   ```sh
   
   ```

   

7. SNS 测试：

```shell
aws sns publish --message file://message.txt --subject Test \
--topic-arn arn:aws:sns:ap-southeast-1:xxxx:lambda-sns-topic-mh
```



8. 