# Dr. Right 資料介接 API Specification

#### Version 1.0.0

本文件根據[The Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0.html)進行授權。

## 公司簡介
Since 2016，Dr. Right 是由精品客服、資深醫師、與數據分析師所組成的團隊。協助醫療院所第一時間與患者關懷溝通，改善院所執行流程、進而提升營運績效，使得醫病雙方都能夠從中受益的 CRM 服務。我們期許能用創新技術與高端服務思維，來打造美好的醫病互動關係。

在網路社群越來越開放的環境底下，醫病關係反而是逐漸惡化的。
 
醫師與患者間，經常是因為就診溝通時的誤解或是不順暢，患者們就直接上網發出公開的負面評論。醫師們也因此感到挫折甚至憤怒，最後轉為雙方對簿公堂。因而往往患者的疑問沒得到解答，醫師也陷入情緒中無法專心看診，社群平台上盡是充斥著醫病關係的仇恨言論。
 
Dr. Right 為醫病間搭起了一個新橋樑，患者離診後有任何疑問或是不愉快，都可以透過專屬的手機應用程式直接反映給院所端。溫馨的醫療客服團隊會立即在黃金 48 小時內，協助醫療團隊透過電話關心病患的現況、照顧不安的情緒、協助釐清問題確切點後，馬上反映至院內做後續處理。不但即時解決醫病雙方資訊不對稱的問題，醫療單位也因此有依據來改善醫療品質。
 
我們希望透過這個服務，讓整個社會產生更多的好醫師與好病患。醫病關係能不再緊張，民眾也能夠接受到更好的醫療品質照護 !

公司里程碑
2016.01：
公司團隊成立，致力協助牙醫師來經營醫病互動關係。

2017.06：
推出醫療輿情分析網站[www.drright.me](https://www.drright.me)，累計服務超過 500 萬次消費者尋醫需求，以及 20萬次的醫病媒合。

2017.09：
累計超過 5,000萬則醫療健康評價分析的經驗，取得與 Google 在醫療評價領域技術合作關係，亦為台灣唯一合作之軟體公司。

2017.10：
聘請[瀛睿律師事務所](http://www.wiseteam.tw)簡榮宗律師擔任法律顧問，守護各個服務環節的適法性。

2017.11：
推出全台首創之醫療精準關懷服務，協助診所業主 e 化經營醫病關係與改善醫療品質。

2018.08：
服務已超過 10 間大型醫療連鎖體系，榮獲經濟部 2018年破殼而出之企業推薦獎。

2018.11：
與[瑞恩克勞 Raincloud 公司](https://yaya.raincloud.tw/yayainfo/)技術合作，整合約診管理服務，讓醫療CRM 解決方案更趨完整。

2018.12：
服務至今已超過 20 家醫療體系集團，涵蓋了北中南最大型連鎖牙醫體系以及教學醫院，皆為地區經營績效 Top 3 之領導醫療機構。

2019.04：
與中國區醫療上市集團策略合作，正式進入中國市場，於廈門開展第一家口腔醫院的服務。

2019.10：
與中國徐州醫科大學技術合作，開展華中地區牙科醫療品質提升專案，陸續導入精準關懷服務於 Dr. Right 品質認證的口腔醫院。

2020.04：
累積處理超過 5 萬則醫療客訴案件，領先業界獨家推出「診所品質工作坊」，協助更多醫療從業人員打造醫病好關係。

2020.10：
版圖開始擴及中醫領域，與風澤中醫集團合作，讓民眾在接受傳統醫學時，亦能獲得令人感動的診後真人關懷服務。

2021.01：
參與台灣經濟研究院執行之[社會創新平台](https://si.taiwan.gov.tw/)，成為社會創新組織持續為醫病和諧關係努力，今年起亦將盈餘之 10% 捐作社會公益使命。

更多資訊，請參考[Dr.Right官網](https://www.drright.club/)


## API 簡介
本 API 規格是用於描述合作診所或第三方公司(以下簡稱為使用者)做資料介接時，於開發對應功能API所需要之設計情境與目標，傳遞或接收資料時之格式文件。

使用標準 HTTP 回應代碼進行回應以指示錯誤。

所有資料傳遞與接收都是使用 JSON 物件方式呈現並且遵照 JSON 標準。

## 目錄

- [身分認證](#authentication)
	- [定義](#authDefinition)
	- [方法](#authMethod)
	- [參數](#authParams)
	- [回應代碼](#authHttpCodes)
	- [回應資料](#authResult)
- [上傳病歷資料](#postPatientInfo)
	- [定義](#postPIDefinition)
	- [方法](#postPIMethod)
	- [參數](#postPIParams)
	- [上傳資料值](#postPIData)
	- [回應代碼](#postPIHttpCodes)
	- [回應資料值](#postPIResult)

- [附錄 A: 修訂歷史](#revisionHistory)


## <a name="authentication"></a>身分認證

#### <a name="authDefinition"></a>定義
身分認證的目的是用來認證使用者的身分，進行所有 API 呼叫時，都必須包含身分認證碼(token)，以確認此次呼叫的合法性。

身分認證碼的有效期為 4小時，過期需要重新取得。

#### <a name="authMethod"></a>方法
Method: `GET`

URL: https://HOST/id/{id}/auth_code/{auth_code}

#### <a name="authParams"></a>參數
id 為使用者所擁有之唯一值，用來代表該單位。

auth_code 為使用者所擁有之唯一值，用來取得身分認證碼時使用。

#### <a name="authHttpCodes"></a>回應代碼
身分認證的回應代碼與其定義如下:
```
200: success
400: bad request
401: wrong id or auth_code
405: method not allowed
```

#### <a name="authResult"></a>回應資料
身分認證的回應資料為一JSON物件，僅包含 token 鍵值對，例如:
```json
{
   "token": "sdDEqdw3Rcoje8Rb9265Gyrxfd3dJoevnY64Udrg6TgyHuJwSe34Rt"
}
```

## <a name="postPatientInfo"></a>上傳病歷資料

#### <a name="postPIDefinition"></a>定義
病歷資料可用來做多種經營管理的績效分析，也可依需要使用在滿意度調查與患者關係管理上，若資料為敏感資料，必須在發送前做部分加密處理。

所有資料皆符合一次性使用原則，不會保存。


#### <a name="postPIMethod"></a>方法
Method: `POST`

URL: https://HOST/hospital/{hosp_id}/token/{token}/patient_info


#### <a name="postPIParams"></a>參數
hosp_id 為該病歷資料所保有之診所id，需要先行定義，可使用多種格式，例如健保署醫事代碼。

token 為先前取得的身分認證碼。


#### <a name="postPIData"></a>上傳資料值
上傳資料值為一 JSON 物件，僅包含 patients 鍵值對，其值為一陣列，可包含多筆病歷資料。

每筆病歷資料皆為一 JSON 物件，必須包含完整的病歷資料。
```json
{
   "patients": [
   	{
		"patient_id": "000000001",
		"name": "Cindy Pool",
		"sex": "F",
		""
	
	}
   ]
}
```


#### <a name="postPIHttpCodes"></a>回應代碼
身分認證的回應代碼與其定義如下:
```
200: success
400: bad request
401: wrong id or auth_code
405: method not allowed
```

#### <a name="postPIResult"></a>回應資料
身分認證的回應資料為一JSON物件，僅包含 token 鍵值對，例如:
```json
{
   "token": "sdDEqdw3Rcoje8Rb9265Gyrxfd3dJoevnY64Udrg6TgyHuJwSe34Rt"
}
```



