# stoplight



```
pbpaste | jq .
history | grep rm
```







  1.为什么成本中心这里GCP和K8S分开算？

​	因为 VM 是公用的，所以不分开的话，不能对应到组

2. 如果算GCP这块的成本的话，还是要勾选K8S 这块的对吗

   这个你们组的情况。如果你们组 GKE 是独享的，其实不用算 K8S 了。直接使用 GCP 就好了

   

不过就你们组比较特殊，如果是其他组就是要算上 K8S

你可以简单的看看有没有重复计算的场景





不会有偏差，主要是你们组的问题

GCP K8S VM 是算你们组的，所以就会有重复计算这块。其他组没这个问题

你可以简单的看下下面的标签就好了





待理解概念：

- GKE

Google kubernets Engine



```
jq '. + {delivery_type:null}' tests/spiders/responses/topyou/topyou_200_TYZPH0006795023YQ.json | sponge tests/spiders/responses/topyou/topyou_200_TYZPH0006795023YQ.json
```



需要批量对 json 文件增加一个字段

```shell
#!/bin/zsh
for jsonfile in /Users/jy.hong/Code/company_projects/couriers-crawlers.aftershipapi.com/tests/spiders/responses/*/*.json;
do
#  echo "$jsonfile"
  jq '. + {delivery_type:null}' "$jsonfile" | sponge "$jsonfile"
done;

```



```
{"a":1}
```





```
openapi: 3.1.0
info:
  title: parser
  version: '1.0'
  summary: parser
servers:
  - url: 'https://couriers-crawlers.aftershipapi.com'
paths:
  '/parsers/{slug}':
    parameters:
      - schema:
          type: string
        name: slug
        in: path
        required: true
    post:
      summary: ''
      operationId: post-parsers-slug
      responses:
        '200':
          description: OK
      requestBody:
        content:
          application/json:
            schema:
              type: object
              properties:
                additional_fields:
                  oneOf:
                    - type: 'null'
                      properties: {}
                    - $ref: ./trackings.yaml#/components/schemas/additional_fields
                tracking_number:
                  type: string
                tracking_payload:
                  type: string
              required:
                - additional_fields
                - tracking_number
                - tracking_payload
      parameters:
        - schema:
            type: string
            enum:
              - application/json
            default: application/json
          in: header
          name: Content-Type
        - schema:
            type: string
          in: header
          name: x-api-key
          required: true
components:
  schemas: {}

```

