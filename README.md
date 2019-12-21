## API SPEC TEMPLATE

### 起動方法
`docker-compose up`

### 起動先

swagger-ui : 
http://127.0.0.1:8082/

swagger-editor : 
http://127.0.0.1:8081/

内部API : 
http://127.0.0.1:8083/pets/1

外部API(CORS対策済み) : 
http://127.0.0.1:8084/pets/1



### 使い方
1. 好きなエディタでswagger/openapi.yamlを編集
2. uiとapiへ自動反映されている


### 注意
- `http://localhost:8082/`で参照するとキャッシュで変更が反映されない場合があるので`http://127.0.0.1:8082/`で参照した方が良い(apiも同様)
- キャッシュクリアして更新はctrl-shift-R(mac)
- swagger-apiを他ドメインからアクセスしたい場合は(CORS対策)、swagger-nginx経由でswagger-apiにアクセスする


### 動作確認

  ```json
  * 例
  curl -i -X GET http://127.0.0.1:8084/pets/1 -H "accept: application/json"

  HTTP/1.1 200 OK
  Server: nginx/1.15.3
  Date: Thu, 04 Oct 2018 07:58:19 GMT
  Content-Type: application/json
  Content-Length: 49
  Connection: keep-alive
  Access-Control-Allow-Origin: *
  Access-Control-Allow-Methods: POST, GET, PATCH, DELETE, PUT, OPTIONS
  Access-Control-Allow-Headers: Origin, Authorization, Accept
  Access-Control-Allow-Credentials: true

  {
    "id": 1,
    "name": "doggie",
    "tag": "dog"
  }
 ```
