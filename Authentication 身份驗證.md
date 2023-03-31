# Authentication 身份驗證
## 身份驗證: Token、Session
身份驗證指要求用戶登錄才能訪問某些信息。  	
為確認身份，用戶必須提供只有用戶和服務器知道的信息（身份驗證因子，ex: 用戶名, 密碼）。  	
常見的身份驗證有兩種方式：  	
1. 基於Session
2. 基於Token
### Token
token 相當於加密過的session紀錄，含有 	
	1. 用戶id
	2. token 簽發時間
	3. 有效期限
任何帶有該token的請求，都會被服務端認為是來自用戶9527的消息，直到1天之後，該token過期失效，服務端將不在認可其代表的用戶身份。  	
```
{
  // 身份信息
  user_id: 9527,
  // Token元信息
  issued_at: '2012年3月5号12点整',
  expiration_time: '1天'
}
// 加密后
895u3485y3748%^HGdsbafjhb	
```	
### 基於Token 的驗證方式
登入流程：  	
1. 客戶端使用帳號、密碼登入，服務端根據用戶信息生成token，發送給客戶端。
2. 客戶端儲存好token，並在之後的數據請求上帶上token。  	

數據操作流程：  	
1. 客戶端在請求用戶信息時上帶上token，發送給服務端。
2. 服務端接到請求後，解析token得出用戶身份，返回數據或操作結果給客戶端。  	

註銷流程：  	  	  	  	
客戶端帶上token，發送給服務端，服務端將token註銷。  	
### Json Web Token(JWT)
Json Web Token 是一種比較受歡迎的token通信規範，用來安全地表示要在雙方傳遞消息的聲明，能夠通過url傳輸。  	  	
JWT的組成有3個部分：
```
Header.Payload.Signature.
```
用.來隔開3個部分。
1. Header:
	- 表示token相關的基本信息。ex: token類型、加密方式（算法）。
	- typ: token type
	- cty: content type
	- alg: Message authentication code algorithm
2. Payload:
   - token 攜帶的數據，及其他token元信息。
   - iss: issuer，簽發方
   - sub: subject，token信息主題
   - aud: audience，接收方
   - exp: expiration time，過期時間
   - nbf: Not(valid) before，生效時間
   - iat: issued at，生成時間
   - jti: JWT ID，唯一標示
	
3. Signature
## 後端傳輸
服務端生成token之後，放在響應體response body，傳遞到客戶端。  	

客戶端收到之後，將token存放在 LocalStorage/SessionStorage中，之後請求數據時，將token放在請求頭的Authentication字段裡待到服務端。  	
```
Authorization: Bearer <jwt_token>
```
服務端收到數據請求後，從Authorization字段中取出token，並驗證其合法性，解析token內容，獲取用戶身份。

### 驗證token

驗證 token合法性需要確認:
1. token有沒有過期
2. 是不是自己簽發的

從payload部分解析，用Base64 解碼出iat, nbf, exp三個時間段。
檢查是否有滿足以下關係：
iat(簽發時間) <= nbf(生效時間) < 當前時間 < exp 過期時間


接著取出token的前2個部分(Header.Payload)，再計算一次簽名(Signature)，看計算結果是否一致。
	
	
http://www.ayqy.net/blog/token-based-login/
