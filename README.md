# Dr. Right Open Medical CRM API Specification

#### Version 1.0.0

本文件根據 [The Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0.html) 進行授權。

## 公司簡介
Since 2016 ，[Dr. Right](https://www.drright.club) 是由數據分析師、資深醫師、與精品客服所組成的團隊。以即時且精準的數據來協助醫療院所在第一時間與患者關懷溝通，改善院所執行流程、進而提升營運績效，使得醫病雙方都能夠從中受益的 CRM 服務。我們期許能用創新技術與高端服務思維，來打造美好的醫病互動關係。

在醫療 CRM 的領域中，我們不斷地耕耘精進，至 2021 年已累積超過上億則的醫療評論處理分析、超過 20,000+ 則的醫病溝通案件處理、以及協助醫療院所改善了超過 6,000+件重大醫療品質問題。背後所仰仗的正是我們自主開發的雲端醫療 CRM 系統。在這五年來於大中華區驗證了 Top10 醫療體系聯盟之後，我們決定將軟體的資料介面，Open Medical CRM API，開放出來，讓更多的醫療軟體商能夠合作共享這些已執行的經驗，並結合多方的技術經驗共同維護這個開放醫療 CRM 的標準。使之越來越成熟進步，一起為醫療 CRM 領域持續耕耘，讓全世界持續產生更多的好醫師與好病患!


#### 技術研發里程碑

2016.01：
公司團隊成立，致力協助醫療院所來經營醫病互動關係。

2017.09：
累計超過 5,000 萬則醫療健康評價分析的經驗，取得與 Google 在醫療評價領域技術合作關係，亦為台灣唯一合作之軟體公司。

2017.11：
推出大中華區首創之 [醫療精準關懷服務](https://www.drright.club)，協助診所業主 e 化經營醫病關係與改善醫療品質。

2018.07：
實踐符合 HIPAA (The Health Insurance Portability & Accountability Act) 資訊安全等級的雲端服務架構。

2018.09：
實踐與醫療資訊系統 HIS (Hospital Information System) 即時處理資訊之效能完全優化，患者即時回饋監聽可小於 5 分鐘，並於 48 小時內持續監控後續 follow up。

2018.11：
實踐連鎖體系管理功能，透過整合式的圖表分析，讓總管理者能夠即視各個分院的狀態與數據分析。 

2019.02：
與中國區醫療上市集團策略合作，完成中國區的服務版本，正式進入中國市場。

2019.07：
與中國微信合作，將微信小程序與醫療精準關懷服務結合，讓醫療院所擁有更多維繫醫病關係的管道。

2020.02：
實踐醫療人員教育訓練管理功能，能持續在醫療現場對於課後目標進行管理，確保醫療品質能有效提升。 

2020.08：
實踐院所經營管理數據分析，讓業主能精確地掌握忠誠客戶的變化，以及客戶回診率等重要指標，讓院所經營改善方向更有所本。

2021.01：
累積上億則的真實醫療互動數據庫後，我們將真正被民眾推薦的好醫師，集結在 [推薦好醫師](https://www.drright.me) 平台上。有別於一般的醫療行銷資訊平台，此為唯一結合線上與線下民眾真實滿意度所打造的尋醫服務。

2021.08：
推薦好醫師平台再次締造新的里程碑，累計服務超過 3,000 萬次消費者尋醫需求，以及 100 萬次的醫病媒合，民眾就診後滿意度平均高達 82.7% 。



## API 簡介
為了提供即時且精準的醫療分析數據，以協助院所做好院內管理與患者關係維繫，我們不停的優化與研發更多的新功能，讓我們的醫療精準關懷服務系統，不只是一個線上與線下的評論即時監管系統，更包含了來診病患數據分析、經營成效分析、多分院管理系統、患者關係管理系統等，讓院所擁有醫療體系的健康檢查機制。不管是對內管理或是對外維護病患關係，都有精準且快速的軟體輔助工具與數據來協助業主達成滿意的目標。

現在，我們將此系統內的 API 架構開放出來，希望能透過這份開放式醫療 CRM API 規格文件，讓醫療體系與各開發者能夠共同合作，集結成一個醫病溝通的大數據平台，節省過去各家業者因不同資料的格式，所需進行介面修改的成本。期望大家能將軟體技術致力於資料分析與流程改善上，讓整個醫療環境能夠向雲端與數據化服務的新時代邁進。

本 API 規格是用於描述合作醫療院所或第三方公司(以下簡稱為使用者)做資料介接時，於開發對應功能 API 所需要之設計情境與目標，傳遞或接收資料時之格式文件。

使用標準 HTTP 回應代碼進行回應以指示錯誤。

所有資料傳遞與接收都是使用 JSON 物件方式呈現並且遵照 JSON 標準。

## 目錄

- [資安認證](#authentication)<!--身分認證-->
	- [定義](#authDefinition)
	- [方法](#authMethod)
	- [參數](#authParams)
	- [回應代碼](#authHttpCodes)
	- [回應資料](#authResult)
- [Facebook 粉專評論代理](#FacebookReviewsMonitor)
	- [定義](#frmDefinition)
	- [方法](#frmMethod)
	- [參數](#frmParams)
	- [回應代碼](#frmHttpCodes)
	- [回應資料](#frmResult)
- [Google 商家評論代理](#GoogleReviewsMonitor)
	- [定義](#grmDefinition)
	- [方法](#grmMethod)
	- [參數](#grmParams)
	- [回應代碼](#grmHttpCodes)
	- [回應資料](#grmResult)
- [匯入病歷資料](#postPatientInfo)
	- [定義](#postPIDefinition)
	- [方法](#postPIMethod)
	- [參數](#postPIParams)
	- [匯入資料](#postPIData)
	- [回應代碼](#postPIHttpCodes)
	- [回應資料](#postPIResult)
- [匯入看診資料](#postOperationInfo)
	- [定義](#postODefinition)
	- [方法](#postOMethod)
	- [參數](#postOParams)
	- [匯入資料](#postOData)
	- [回應代碼](#postOHttpCodes)
	- [回應資料](#postOResult)
- [匯入評論資料](#postReviews)
	- [定義](#postReviewsDefinition)
	- [方法](#postReviewsMethod)
	- [參數](#postReviewsParams)
	- [匯入資料](#postReviewsData)
	- [回應代碼](#postReviewsHttpCodes)
	- [回應資料](#postReviewsResult)
- [匯出評論處理結果](#getReviewResult)
	- [定義](#getRRDefinition)
	- [方法](#getRRMethod)
	- [參數](#getRRParams)
	- [匯入資料](#getRRData)
	- [回應代碼](#getRRHttpCodes)
	- [回應資料](#getRRResult)
- [匯入約診提醒資料](#postAppointmentReminder)
	- [定義](#postARDefinition)
	- [方法](#postARMethod)
	- [參數](#postARParams)
	- [匯入資料](#postARData)
	- [回應代碼](#postARHttpCodes)
	- [回應資料](#postARResult)
- [匯出約診病患回覆結果](#getAppointmentReminderResult)
	- [定義](#getARRDefinition)
	- [方法](#getARRMethod)
	- [參數](#getARRParams)
	- [上傳資料](#getARRData)
	- [回應代碼](#getARRHttpCodes)
	- [回應資料](#getARRResult)
- [匯出約診分析資料](#getAppointmentAnalysisResult)
	- [定義](#getAARDefinition)
	- [方法](#getAARMethod)
	- [參數](#getAARParams)
	- [匯入資料](#getAARData)
	- [回應代碼](#getAARHttpCodes)
	- [回應資料](#getAARResult)
- [匯出滿意度分析資料](#getClinicSatisfaction)
	- [定義](#getCSDefinition)
	- [方法](#getCSMethod)
	- [參數](#getCSParams)
	- [匯入資料](#getCSData)
	- [回應代碼](#getCSHttpCodes)
	- [回應資料](#getCSResult)

- [附錄 A: 修訂歷史](#revisionHistory)


## <a name="authentication"></a>資安認證

#### <a name="authDefinition"></a>定義
保護使用者的資料安全，是最重要的事，因此不管在做資料的匯入或匯出操作，或是資料的計算與保存時，皆需要以符合 HIPAA 規範的方式來執行，可參考 [HIPAA 安全及合規架構白皮書](https://d1.awsstatic.com/whitepapers/compliance/AWS_HIPAA_Compliance_Whitepaper.pdf)。

資安認證的目的是用來認證使用者的身分，進行所有 API 呼叫時，都必須包含身分認證碼(token)，以確認此次呼叫的合法性。

#### <a name="authMethod"></a>方法
Method: `GET`

URL: https://HOST/id/{id}/auth_code/{auth_code}/security_mode/{security_mode}

#### <a name="authParams"></a>參數
id 為使用者所擁有之唯一值，用來代表該單位。

auth_code 為使用者所擁有之唯一值，用來取得身分認證碼時使用。

security_mode 為資安等級指名之模式。

#### <a name="authHttpCodes"></a>回應代碼
資安認證的回應代碼與其定義如下:
```
200: success
400: bad request
401: wrong id or auth_code
405: method not allowed
```

#### <a name="authResult"></a>回應資料
資安認證的回應資料為一 JSON 物件，僅包含 token 鍵值對，例如:
```json
{
   "token": "sdDEqdw3Rcoje8Rb9265Gyrxfd3dJoevnY64Udrg6TgyHuJwSe34Rt"
}
```


## <a name="FacebookReviewsMonitor"></a>Facebook 粉專評論代理

#### <a name="frmDefinition"></a>定義
Facebook 粉專為 Facebook 粉絲專頁的縮寫，透過此 API ，您可將 Facebook 粉專的評論直接交由 Dr. Right 來維護與管理，Dr. Right 的 Facebook 粉專即時監控系統，在評論發生的當下，就會即時收到並及時掌握與立即處理，讓您不用在為如何回覆評論而煩惱。

#### <a name="frmMethod"></a>方法
Method: `POST`

URL: https://HOST/id/{id}/auth_code/{auth_code}/page_id/{page_id}/page_token/{page_token}

#### <a name="frmParams"></a>參數
id 為使用者所擁有之唯一值，用來代表該單位。

auth_code 為使用者所擁有之唯一值，用來取得身分認證碼時使用。

page_id 為使用者的 facebook 粉專的 id。

page_token 為使用者的 facebook 粉專的長效型權杖，詳細資訊可參考 [Facebook 登入](https://developers.facebook.com/docs/facebook-login)中的存取權杖章節。

#### <a name="frmHttpCodes"></a>回應代碼
回應代碼與其定義如下:
```
200: success
400: bad request
401: wrong id or auth_code
405: method not allowed
```

#### <a name="frmResult"></a>回應資料
回應資料為一 JSON 物件，僅包含 result 鍵值對，例如:
```json
{
   "result": "OK"
}
```



## <a name="GoogleReviewsMonitor"></a>Google 商家評論代理

#### <a name="grmDefinition"></a>定義
Dr. Right 取得與 Google 在醫療評價領域技術的合作關係，亦為台灣唯一合作的軟體公司，透過 Dr. Right 來管理您的 Google 我的商家，會是您最明智的選擇。

使用此 API 前，請先將 Dr. Right 加入您的商家管理者後，再透過此 API 將 Google 我的商家 與 Dr. Right 做綁定，Dr. Right 的 Google 商家即時監控系統，在評論發生的當下，就會即時收到並及時掌握與立即處理，讓您不用在為如何回覆評論而煩惱。

#### <a name="grmMethod"></a>方法
Method: `POST`

URL: https://HOST/id/{id}/auth_code/{auth_code}/gmb_id/{gmb_id}

#### <a name="grmParams"></a>參數
id 為使用者所擁有之唯一值，用來代表該單位。

auth_code 為使用者所擁有之唯一值，用來取得身分認證碼時使用。

gmb_id 為使用者的 Google 商家的 location id。

#### <a name="grmHttpCodes"></a>回應代碼
回應代碼與其定義如下:
```
200: success
400: bad request
401: wrong id or auth_code
405: method not allowed
```

#### <a name="grmResult"></a>回應資料
回應資料為一 JSON 物件，僅包含 result 鍵值對，例如:
```json
{
   "result": "OK"
}
```






## <a name="postPatientInfo"></a>匯入病歷資料

#### <a name="postPIDefinition"></a>定義
病歷資料可依需要使用在滿意度調查與患者關係管理上，也可用來做多種經營管理的績效分析。

所有資料皆符合一次性使用原則，不會保存。

#### <a name="postPIMethod"></a>方法
Method: `POST`

URL: https://HOST/hospital/{hosp_id}/token/{token}/patient_info


#### <a name="postPIParams"></a>參數
hosp_id 為該病歷資料所保有之診所 id，需要先行定義，可使用多種格式，例如健保署醫事代碼。

token 為先前取得的身分認證碼。


#### <a name="postPIData"></a>匯入資料
匯入資料值為一 JSON 物件，僅包含 patients 鍵值對，其值為一陣列，可包含多筆病歷資料。

每筆病歷資料皆為一 JSON 物件，必須包含完整的病歷內容。

例如:
```json
{
   "patients" : [
   	{
		"patient_id" : "000000001",
		"name" : "Cindy Pool",
		"sex" : "F",
		"birthday" : "1971-03-27",
		"phone" : "0912345678",
		"first_visit_date" : "2019-07-12",
		"visit_times" : "5",
		"doctor_name" : "Roger Kingdom",
		"reserved_1": "TBD",
		"reserved_2": "TBD",
		"reserved_3": "TBD",
	}
   ]
}
```


#### <a name="postPIHttpCodes"></a>回應代碼
上傳病歷資料的回應代碼與其定義如下:
```
201: success
400: bad request
401: unauthorized
404: wrong hosp_id
405: method not allowed
```

#### <a name="postPIResult"></a>回應資料
上傳病歷資料無回應資料



## <a name="postOperationInfo"></a>匯入看診資料

#### <a name="postODefinition"></a>定義
看診資料可依需要使用在滿意度調查與患者關係管理上，也可用來做多種經營管理的績效分析。

所有資料皆符合一次性使用原則，不會保存。


#### <a name="postOMethod"></a>方法
Method: `POST`

URL: https://HOST/hospital/{hosp_id}/token/{token}/operation_data


#### <a name="postOParams"></a>參數
hosp_id 為該病歷資料所保有之診所 id，需要先行定義，可使用多種格式，例如健保署醫事代碼。

token 為先前取得的身分認證碼。


#### <a name="postOData"></a>匯入資料
匯入看診資料值為一 JSON 物件，僅包含 operation 鍵值對，其值為一陣列，可包含多筆病歷資料。

每筆病歷資料皆為一 JSON 物件，必須包含完整的病歷內容。

例如:
```json
{
   "operation" : [
   	{
		"patient_id" : "000000001",
		"name" : "Cindy Pool",
		"check_in_datetime" : "2021-07-29 10:23",
		"check_out_datetime" : "2021-07-29 11:11",
		"doctor_name" : "Roger Kingdom",
		"reserved_1": "TBD",
		"reserved_2": "TBD",
		"reserved_3": "TBD",
		"reserved_4": "TBD",
		"reserved_5": "TBD",
	}
   ]
}
```

#### <a name="postOHttpCodes"></a>回應代碼
上傳看診資料的回應代碼與其定義如下:
```
201: success
400: bad request
401: unauthorized
404: wrong hosp_id
405: method not allowed
```

#### <a name="postOResult"></a>回應資料
上傳看診資料無回應資料


## <a name="postReviews"></a>匯入評論資料

#### <a name="postReviewsDefinition"></a>定義
評論資料的來源可為線上取得，如: Facebook 與 Google 等社群媒體，也可為線下取得，如透過即時滿意度調查系統或問卷等。

評論資料可用來做多種經營管理的績效分析。

評論不論正、負評，皆可委託 Dr. Right 專業的醫病關係客服人員處理，處理進度與結果由 [取得評論處理結果](#getReviewResult) API 獲得。

所有資料皆依據與使用者約定方式處理。

#### <a name="postReviewsMethod"></a>方法
Method: `POST`

URL: https://HOST/hospital/{hosp_id}/token/{token}/reviews

#### <a name="postReviewsParams"></a>參數
hosp_id 為該病歷資料所保有之診所 id，需要先行定義，可使用多種格式，例如健保署醫事代碼。

token 為先前取得的身分認證碼。

#### <a name="postReviewsData"></a>匯入資料
匯入資料值為一 JSON 物件，僅包含 reviews 鍵值對，其值為一陣列，可包含多筆評論資料。

每筆評論資料皆為一 JSON 物件，必須包含完整的評論內容。

例如:
```json
{
   "reviews" : [
   	{
		"source" : "Facebook",
		"author" : "Irene Huang",
		"rating" : "5",
		"create_datetime" : "2021-07-26 14:32",
		"content" : "服務太棒了，尤其是跟診助理超級細心的，不像之前遇到的都會讓我被口水嗆到，結束後還有給我刷牙的衛教知識，非常滿意",
		"reserved_1": "TBD",
		"reserved_2": "TBD"
	},
	{
		"source" : "Survey",
		"author" : "黃美涓",
		"rating" : "1",
		"create_datetime" : "2021-07-24 11:36",
		"content" : "有打去問.到現場掛 等了快2小時",
		"doctor" : "李文政",
		"reserved_1": "TBD",
		"reserved_2": "TBD"
	}
   ]
}
```


#### <a name="postReviewsHttpCodes"></a>回應代碼
上傳評論資料的回應代碼與其定義如下:
```
201: success
400: bad request
401: unauthorized
404: wrong hosp_id
405: method not allowed
```

#### <a name="postReviewsResult"></a>回應資料
上傳評論資料的回應資料，為一 JSON 物件，僅包含 results 鍵值對，其值為一陣列，包含多筆評論資料的回應資料。

每筆回應資料，皆為一 JSON 物件，包含其評論內容中的 source/author/create_datetime 外，在加上其 id。

id 為未來查詢時使用，請妥善保存。

例如:
```json
{
   "results" : [
   	{
		"source" : "Facebook",
		"author" : "Irene Huang",
		"create_datetime" : "2021-07-26 14:32",
		"id" : "dD54Ddt7Yxe#dfu$e32QaFguyuRew43Mhe",
		"reserved_1": "TBD",
		"reserved_2": "TBD",
		"reserved_3": "TBD"
	},
	{
		"source" : "Survey",
		"author" : "黃美涓",
		"create_datetime" : "2021-07-24 11:36",
		"id" : "r4dEihR53Wshi7IqaE41wPli9rFex1Erts",
		"reserved_1": "TBD",
		"reserved_2": "TBD",
		"reserved_3": "TBD"
	}
   ]
}
```


## <a name="getReviewResult"></a>匯出評論處理結果

#### <a name="getRRDefinition"></a>定義
上傳評論資料後，在處理成效最好的黃金 48 小時內，隨時都能透過此 API 取得評論的處理狀態與結果。

所有資料皆依據與使用者約定方式處理。

#### <a name="getRRMethod"></a>方法
Method: `GET`

URL: https://HOST/hospital/{hosp_id}/token/{token}/{review_id}/result/

#### <a name="getRRParams"></a>參數
hosp_id 為該病歷資料所保有之診所 id，需要先行定義，可使用多種格式，例如健保署醫事代碼。

token 為先前取得的身分認證碼。

review_id 為先前上傳評論資料時取得的評論 id。

#### <a name="getRRData"></a>匯入資料
取得評論處理結果無匯入資料

#### <a name="getRRHttpCodes"></a>回應代碼
取得評論處理結果的回應代碼與其定義如下:
```
201: success
400: bad request
401: unauthorized
404: wrong hosp_id
405: method not allowed
```

#### <a name="getRRResult"></a>回應資料
取得評論處理結果的回應資料，為一 JSON 物件，僅包含 result 鍵值對，其值為一 JSON 物件，包含此評論資料的處理狀態或處理完成的結果。

例如:
```json
{
   "result" : {
		"status" : "Done",
		"source" : "Survey",
		"author" : "黃美涓",
		"create_datetime" : "2021-07-24 11:36",
		"reply" : "[病人主訴] 因牙痛難耐致電診所，同仁表示你現在趕快過來現在沒有人，結果卻又等了兩小時(病人住診所後棟) [目前狀況] 1. 牙痛來緊急處置，因太痛了醫師無法下手清理，被告知回去消炎後再來抽神經，但未說明要注意甚麼? 何時再過來? 2. 患者焦慮表示為什麼不打麻藥後進行抽神經? 和患者說明當下醫師欲進行緊急處置與消炎的原因後，患者安心許多，會先按時吃藥觀察，並注意清潔。[院內追蹤] 1. 因為醫師沒有告知甚麼時候回診，也沒說明''可以回診的區間日期''，希望同仁能協助和醫師確認一下，並且先致電預約。 2. 病人晚上的時間都可配合，還請同仁今天幫忙回電病人唷!",
		"reserved_1": "TBD",
		"reserved_2": "TBD",
		"reserved_3": "TBD",
		"reserved_4": "TBD"
	}
}
```



## <a name="postAppointmentReminder"></a>匯入約診提醒資料

#### <a name="postARDefinition"></a>定義
約診提醒的作用是用來善意的提醒病患，其下次看診當天的報到時間、地點與看診時應注意的事項等資訊。

約診提醒可以透過簡訊、Line、Email 與 APP 等多種全面性的管道來通知病患。

所有資料皆依據與使用者約定方式處理。

#### <a name="postARMethod"></a>方法
Method: `POST`

URL: https://HOST/hospital/{hosp_id}/token/{token}/ap_reminder

#### <a name="postARParams"></a>參數
hosp_id 為該病歷資料所保有之診所 id，需要先行定義，可使用多種格式，例如健保署醫事代碼。

token 為先前取得的身分認證碼。

#### <a name="postARData"></a>匯入資料
資料值為一 JSON 物件，僅包含 reminders 鍵值對，其值為一陣列，可包含多筆約診資料。

每筆約診資料皆為一 JSON 物件，必須包含完整的約診內容。

例如:
```json
{
   "reminders" : [
   	{
		"patient" : "張皓",
		"patient_id" : "000005439",
		"appointment_datetime" : "2021-08-13 19:00",
		"send_msg_datetime" : "2021-08-12 09:30",
		"doctor_name" : "李文政",
		"special_reminder" : "請攜帶矯正費用 15,000 圓",
		"notification_method" : "1",
		"reserved_1": "TBD",
		"reserved_2": "TBD",
		"reserved_3": "TBD",
	},
	{
		"patient" : "林語文",
		"patient_id" : "000010221",
		"appointment_datetime" : "2021-08-13 20:00",
		"send_msg_datetime" : "2021-08-12 09:30",
		"doctor_name" : "黃清清",
		"special_reminder" : "",
		"notification_method" : "2",
		"reserved_1": "TBD",
		"reserved_2": "TBD",
		"reserved_3": "TBD",
	}
   ]
}
```


#### <a name="postARHttpCodes"></a>回應代碼
上傳約診提醒資料的回應代碼與其定義如下:
```
201: success
400: bad request
401: unauthorized
404: wrong hosp_id
405: method not allowed
```

#### <a name="postARResult"></a>回應資料
上傳約診提醒資料的回應資料，為一 JSON 物件，僅包含 results 鍵值對，其值為一陣列，包含多筆約診提醒資料的回應資料。

每筆回應資料，皆為一 JSON 物件，包含其約診提醒資料內容中的 patient_id/appointment_datetime 外，在加上其 id。

id 為未來查詢時使用，請妥善保存。

例如:
```json
{
   "results" : [
   	{
		"patient_id" : "000005439",
		"appointment_datetime" : "2021-08-13 19:00",
		"id" : "dD54Dde8lgR420Hv46Rt2zoeRygh387Thd",
		"reserved_1": "TBD",
		"reserved_2": "TBD"
	},
	{
		"patient_id" : "000010221",
		"appointment_datetime" : "2021-08-13 20:00",
		"id" : "3Rtg63Jipdhi7IqaE41wPli9rFextR53Es",
		"reserved_1": "TBD",
		"reserved_2": "TBD"
	}
   ]
}
```


## <a name="getAppointmentReminderResult"></a>匯出約診病患回覆結果

#### <a name="getARRDefinition"></a>定義
上傳約診提醒資料後，以此 API 取得病患的回覆結果。

所有資料皆依據與使用者約定方式處理。

#### <a name="getARRMethod"></a>方法
Method: `GET`

URL: https://HOST/hospital/{hosp_id}/token/{token}/ap_reminder/{reminder_id}/result/

#### <a name="getARRParams"></a>參數
hosp_id 為該病歷資料所保有之診所 id，需要先行定義，可使用多種格式，例如健保署醫事代碼。

token 為先前取得的身分認證碼。

reminder_id 為先前上傳約診提醒資料時取得的約診提醒 id。

#### <a name="getARRData"></a>匯入資料
取得約診病患回覆結果無匯入資料

#### <a name="getARRHttpCodes"></a>回應代碼
取得約診病患回覆結果的回應代碼與其定義如下:
```
201: success
400: bad request
401: unauthorized
404: wrong hosp_id
405: method not allowed
```

#### <a name="getARRResult"></a>回應資料
取得約診病患回覆結果的回應資料，為一 JSON 物件，僅包含 result 鍵值對，其值為一 JSON 物件，包含此約診提醒的處理狀態與病患的回覆結果。

其中 patient_reply 為病患的回覆結果，共有以下二種可能值:
```
OK: 病患以確認同意此約診資訊
Cancle: 病患取消約診
```

例如:
```json
{
   "result" : {
		"status" : "Done",
		"id" : "dD54Dde8lgR420Hv46Rt2zoeRygh387Thd",
		"patient_id" : "000005439",
		"appointment_datetime" : "2021-08-13 19:00",
		"patient_reply" : "OK",
		"reserved_1": "TBD",
		"reserved_2": "TBD"
	}
}
```







## <a name="getAppointmentAnalysisResult"></a>匯出病患回診分析資料

#### <a name="getAARDefinition"></a>定義
病患回診的狀況，可以看成是病患對診所整體的認同度指標，對診所來說是極具重要性的經營指標之一。

我們依據上傳的各項資料，並配合我們獨家的回診率演算法做統計分析，就可以得到回診率的分項分析資料。

#### <a name="getAARMethod"></a>方法
Method: `GET`

URL: https://HOST/hospital/{hosp_id}/token/{token}/appointmant_analysis/result/

#### <a name="getAARParams"></a>參數
hosp_id 為該病歷資料所保有之診所 id，需要先行定義，可使用多種格式，例如健保署醫事代碼。

token 為先前取得的身分認證碼。

#### <a name="getAARData"></a>匯入資料
取得病患回診分析資料的匯入資料，為一 JSON 物件，僅包含 period 鍵值對，其值為一 JSON 物件，包含統計分析的開始與結束月份。

例如:
```json
{
   "period" : {
		"start" : "2019/01",
		"end" : "2019/12",
		"reserved_1": "TBD"
	}
}
```

#### <a name="getAARHttpCodes"></a>回應代碼
取得病患回診分析資料的回應代碼與其定義如下:
```
201: success
400: bad request
401: unauthorized
404: wrong hosp_id
405: method not allowed
```

#### <a name="getAARResult"></a>回應資料
取得病患回診分析資料的回應資料，為一 JSON 物件，僅包含 result 鍵值對，其值為一 JSON 物件，包含此診所的病患回診分析資料。

例如:
```json
{
   "result" : {
		"total" : "66.3",
		"changed" : "54.2",
		"assigned" : "76.6",
		"reminder_cancled" : "44.1",
		"cancled" : "32.9",
		"黃清清" : "67.3",
		"李文政" : "76.5",
		"余承瑜" : "70.2",
		"黃凱" : "53.2",
		"張藝雯" : "66.4",
		"郭興岑" : "41.1",
		"談艾樺" : "39.2",
		"reserved_1": "TBD",
		"reserved_2": "TBD",
		"reserved_3": "TBD",
	}
}
```



## <a name="getClinicSatisfaction"></a>匯出滿意度分析資料

#### <a name="getCSDefinition"></a>定義
從病患的看診回饋與約診的回覆狀況中，可以抽絲剝繭了解到病患對診所或是各個醫師的認同狀態。

因此滿意度是經營診所非常重要的指標之一。

我們依據使用者所上傳的，還有從社群取得的各項資料，在搭配我們開發的滿意度權重與平衡最佳化演算法做計算與分析，就可以得到診所與醫師的滿意度分項資料。

#### <a name="getCSMethod"></a>方法
Method: `GET`

URL: https://HOST/hospital/{hosp_id}/token/{token}/clinic_satisfaction/result/

#### <a name="getCSParams"></a>參數
hosp_id 為該病歷資料所保有之診所 id，需要先行定義，可使用多種格式，例如健保署醫事代碼。

token 為先前取得的身分認證碼。

#### <a name="getCSData"></a>匯入資料
取得滿意度分析資料無匯入資料

#### <a name="getCSHttpCodes"></a>回應代碼
取得滿意度分析資料的回應代碼與其定義如下:
```
201: success
400: bad request
401: unauthorized
404: wrong hosp_id
405: method not allowed
```

#### <a name="getCSResult"></a>回應資料
取得滿意度分析資料的回應資料，為一 JSON 物件，僅包含 result 鍵值對，其值為一 JSON 物件，包含此診所與醫師的滿意度分項資料。

例如:
```json
{
   "result" : {
		"total" : "81.3",
		"environment" : "86.3",
		"facility" : "78.8",
		"receptionist" : "57.2",
		"assistant" : "82.8",
		"appointment" : "88.4",
		"Endodontics" : "75.2",
		"Orthodontics" : "65.3",
		"Prosthetics" : "81.1",
		"Crowns" : "77.8",
		"Implants" : "67.7",
		"Whitening" : "88.2", 
		"Cleaning" : "82.9",
		"doctor" : "70.1", 
		"黃清清" : "65.3",
		"李文政" : "78.5",
		"余承瑜" : "71.8",
		"黃凱" : "59.9",
		"張藝雯" : "69.5",
		"郭興岑" : "45.2",
		"談艾樺" : "37.8",
		"reserved_1": "TBD",
		"reserved_2": "TBD",
		"reserved_3": "TBD",
	}
}
```

## 開發人員
Jeff Chang
[Jeff Chang](https://www.linkedin.com/in/jeff-chang-9074b2163/)

## <a name="revisionHistory"></a>附錄 A: 修訂歷史

版本 | 日期 | 注解
---|:---|:---
1.0.0   | 2021-07-30 | Open Medical CRM API 規格首次釋出










