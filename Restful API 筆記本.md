# Restful API 筆記本

## Http 狀態碼 Http status code

- 2xx 代表請求成功:
   - 代表請求成功被伺服器接收，理解並接受。
   - 200: 請求已成功，請求希望回應head 或資料，可以隨此回應返回。
- 3xx 代表重新導向：
   - 這類狀態碼代表需要客戶端採取進一步操作，才能完成請求。
   - 302 Found: 要求客戶端執行 臨時的重新導向。
## 客戶端錯誤: 4xx
- 4xx 代表客戶端錯誤：
   - 這類狀態碼代表客戶端可能發生了錯誤，妨礙了伺服器的處理。
   - 400 Bad Request: 由於明顯的客戶端錯誤，伺服器不能或不會處理該請求。ex: 格式錯誤的請求
   - 401 Unauthorized: 未認證(代表未登入)
   - 403 Forbidden: 伺服器已經處理請求，但是拒絕執行它。(代表已登入但是存取權限不足)
   - 404 Not Found: 請求失敗找不到資源
   - 405 Method Not Allowed: 請求行中的請求方法，不能被用於請求相應的資源。(ex: 使用錯誤的HTTP Method而導致的錯誤，原本需要用POST，用了GET)
   
## 伺服器端錯誤: 5xx
- 5xx 代表 伺服器端錯誤
  - 這類狀態碼代表伺服器無法完成有效的請求。
  - 500 Internal Server Error: 通用錯誤信息，沒有給出具體的錯誤資訊。伺服器遇到了未曾預料的狀況，導致他無法完成對請求的處理。
    

| Status Code | Category       | Meaning                                                              |
|-------------|----------------|----------------------------------------------------------------------|
| 1xx         | Informational  | The request has been received and the server is still processing it. |
| 2xx         | Success        | The request was successful and the server has fulfilled it.         |
| 200         | OK             | The request was successful, and the response body contains the requested data or information.      |
| 3xx         | Redirection    | Further action is needed to fulfill the request.                    |
| 301         | Moved Permanently | The requested resource has been permanently moved to a different URL. |
| 302         | Found/Redirect | The requested resource has been temporarily moved to a different URL.|
| 304         | Not Modified   | The requested resource has not been modified since the last request, and the cached version can be used.|
| 4xx         | Client Error   | The client's request contains an error or cannot be fulfilled.      |
| 400         | Bad Request    | The server cannot understand the client's request, often due to malformed syntax.     |
| 404         | Not Found      | The requested resource could not be found on the server.            |
| 5xx         | Server Error   | There was an error on the server while processing the request.      |
| 500         | Internal Server Error | An unexpected error occurred on the server, preventing it from fulfilling the request.     |
| 503         | Service Unavailable | The server is currently unable to handle the request due to  maintenance or overload.       |     

https://ithelp.ithome.com.tw/articles/10241979
