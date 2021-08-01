# Dr. Right Open Medical CRM API Specification

#### Version 1.0.0

本文件根據 [The Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0.html) 進行授權。

## 公司簡介
Since 2016，Dr. Right 是由數據分析師、資深醫師、與精品客服所組成的團隊。以即時且精準的數據來協助醫療院所在第一時間與患者關懷溝通，改善院所執行流程、進而提升營運績效，使得醫病雙方都能夠從中受益的 CRM 服務。我們期許能用創新技術與高端服務思維，來打造美好的醫病互動關係。

<!--在網路社群越來越開放的環境底下，醫病關係反而是逐漸惡化的。
 
醫師與患者間，經常是因為就診溝通時的誤解或是不順暢，患者們就直接上網發出公開的負面評論。醫師們也因此感到挫折甚至憤怒，最後轉為雙方對簿公堂。因而往往患者的疑問沒得到解答，醫師也陷入情緒中無法專心看診，社群平台上盡是充斥著醫病關係的仇恨言論。
 
Dr. Right 為醫病間搭起了一個新橋樑，患者離診後有任何疑問或是不愉快，都可以透過專屬的手機應用程式直接反映給院所端。溫馨的醫療客服團隊會立即在黃金 48 小時內，協助醫療團隊透過電話關心病患的現況、照顧不安的情緒、協助釐清問題確切點後，馬上反映至院內做後續處理。不但即時解決醫病雙方資訊不對稱的問題，醫療單位也因此有依據來改善醫療品質。
 
我們希望透過這個服務，讓整個社會產生更多的好醫師與好病患。醫病關係能不再緊張，民眾也能夠接受到更好的醫療品質照護 !-->

#### 公司里程碑

2016.01：
公司團隊成立，致力協助牙醫師來經營醫病互動關係。

2017.06：
推出醫療輿情分析網站 [www.drright.me](https://www.drright.me)，累計服務超過 500 萬次消費者尋醫需求，以及 20 萬次的醫病媒合。

2017.09：
累計超過 5,000 萬則醫療健康評價分析的經驗，取得與 Google 在醫療評價領域技術合作關係，亦為台灣唯一合作之軟體公司。

2017.10：
聘請[瀛睿律師事務所](http://www.wiseteam.tw)簡榮宗律師擔任法律顧問，守護各個服務環節的適法性。

2017.11：
推出全台首創之醫療精準關懷服務，協助診所業主 e 化經營醫病關係與改善醫療品質。

2018.08：
服務已超過 10 間大型醫療連鎖體系，榮獲經濟部 2018年破殼而出之企業推薦獎。

2018.11：
與[瑞恩克勞 Raincloud 公司](https://yaya.raincloud.tw/yayainfo/)技術合作，整合約診管理服務，讓醫療 CRM 解決方案更趨完整。

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

更多資訊，請參考 [Dr. Right 官網](https://www.drright.club/)


## API 簡介
為了提供即時且精準的分析數據，以協助醫療院所與患者溝通，我們開發了醫療精準關懷服務系統，並將此系統內的 API 架構開放出來，希望能透過這份醫療 CRM API 規格文件，讓醫療體系與第三方協力廠商，能夠共同合作，連結成一個醫病溝通的大數據平台，同時也讓台灣醫療環境能夠向雲端與數據化服務的新時代邁進。

本 API 規格是用於描述合作診所或第三方公司(以下簡稱為使用者)做資料介接時，於開發對應功能 API 所需要之設計情境與目標，傳遞或接收資料時之格式文件。

使用標準 HTTP 回應代碼進行回應以指示錯誤。

所有資料傳遞與接收都是使用 JSON 物件方式呈現並且遵照 JSON 標準。

## 目錄

- [資安認證](#authentication)<!--身分認證-->
	- [定義](#authDefinition)
	- [方法](#authMethod)
	- [參數](#authParams)
	- [回應代碼](#authHttpCodes)
	- [回應資料](#authResult)
- [上傳病歷資料](#postPatientInfo)
	- [定義](#postPIDefinition)
	- [方法](#postPIMethod)
	- [參數](#postPIParams)
	- [上傳資料](#postPIData)
	- [回應代碼](#postPIHttpCodes)
	- [回應資料](#postPIResult)
- [上傳評論資料](#postReviews)
	- [定義](#postReviewsDefinition)
	- [方法](#postReviewsMethod)
	- [參數](#postReviewsParams)
	- [上傳資料](#postReviewsData)
	- [回應代碼](#postReviewsHttpCodes)
	- [回應資料](#postReviewsResult)
- [取得評論處理結果](#getReviewResult)
	- [定義](#getRRDefinition)
	- [方法](#getRRMethod)
	- [參數](#getRRParams)
	- [上傳資料](#getRRData)
	- [回應代碼](#getRRHttpCodes)
	- [回應資料](#getRRResult)
- [上傳約診提醒資料](#postAppointmentReminder)
	- [定義](#postARDefinition)
	- [方法](#postARMethod)
	- [參數](#postARParams)
	- [上傳資料](#postARData)
	- [回應代碼](#postARHttpCodes)
	- [回應資料](#postARResult)
- [附錄 A: 修訂歷史](#revisionHistory)


## <a name="authentication"></a>資安認證

#### <a name="authDefinition"></a>定義
資安認證的目的是用來認證使用者的身分，進行所有 API 呼叫時，都必須包含身分認證碼(token)，以確認此次呼叫的合法性。

身分認證碼的有效期為 4 小時，過期需要重新取得。

#### <a name="authMethod"></a>方法
Method: `GET`

URL: https://HOST/id/{id}/auth_code/{auth_code}

#### <a name="authParams"></a>參數
id 為使用者所擁有之唯一值，用來代表該單位。

auth_code 為使用者所擁有之唯一值，用來取得身分認證碼時使用。

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

## <a name="postPatientInfo"></a>上傳病歷資料

#### <a name="postPIDefinition"></a>定義
病歷資料可用來做多種經營管理的績效分析，也可依需要使用在滿意度調查與患者關係管理上，若資料為敏感資料，必須在發送前做部分加密處理。

所有資料皆符合一次性使用原則，不會保存。


#### <a name="postPIMethod"></a>方法
Method: `POST`

URL: https://HOST/hospital/{hosp_id}/token/{token}/patient_info


#### <a name="postPIParams"></a>參數
hosp_id 為該病歷資料所保有之診所 id，需要先行定義，可使用多種格式，例如健保署醫事代碼。

token 為先前取得的身分認證碼。


#### <a name="postPIData"></a>上傳資料
上傳資料值為一 JSON 物件，僅包含 patients 鍵值對，其值為一陣列，可包含多筆病歷資料。

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
		"check_in_datetime" : "2021-06-03 10:23",
		"check_out_datetime" : "2021-06-03 11:01",
		"doctor_name" : "Roger Kingdom"
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




## <a name="postReviews"></a>上傳評論資料

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

#### <a name="postReviewsData"></a>上傳資料
上傳資料值為一 JSON 物件，僅包含 reviews 鍵值對，其值為一陣列，可包含多筆評論資料。

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
		"content" : "服務太棒了，尤其是跟診助理超級細心的，不像之前遇到的都會讓我被口水嗆到，結束後還有給我刷牙的衛教知識，非常滿意"
	},
	{
		"source" : "Survey",
		"author" : "黃美涓",
		"rating" : "1",
		"create_datetime" : "2021-07-24 11:36",
		"content" : "有打去問.到現場掛 等了快2小時",
		"doctor" : "李文政"
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
		"id" : "dD54Ddt7Yxe#dfu$e32QaFguyuRew43Mhe"
	},
	{
		"source" : "Survey",
		"author" : "黃美涓",
		"create_datetime" : "2021-07-24 11:36",
		"id" : "r4dEihR53Wshi7IqaE41wPli9rFex1Erts"
	}
   ]
}
```


## <a name="getReviewResult"></a>取得評論處理結果

#### <a name="getRRDefinition"></a>定義
上傳評論資料後，以此 API 取得後續的處理狀態與結果。

評論的來源若為線上，處理時間為 48 小時，上傳評論 48 小時後，可取得包含專業的評論回覆內容的結果。

評論的來源若為線下，處理時間為 48 小時至 72 小時，處理完成後，可取得與病患聯繫的狀況與處理結果。

所有資料皆依據與使用者約定方式處理。

#### <a name="getRRMethod"></a>方法
Method: `GET`

URL: https://HOST/hospital/{hosp_id}/token/{token}/{review_id}/result/

#### <a name="getRRParams"></a>參數
hosp_id 為該病歷資料所保有之診所 id，需要先行定義，可使用多種格式，例如健保署醫事代碼。

token 為先前取得的身分認證碼。

review_id 為先前上傳評論資料時取得的評論 id。

#### <a name="getRRData"></a>上傳資料
取得評論處理結果無上傳資料

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
		"reply" : "[病人主訴] 因牙痛難耐致電診所，同仁表示你現在趕快過來現在沒有人，結果卻又等了兩小時(病人住診所後棟) [目前狀況] 1. 牙痛來緊急處置，因太痛了醫師無法下手清理，被告知回去消炎後再來抽神經，但未說明要注意甚麼? 何時再過來? 2. 患者焦慮表示為什麼不打麻藥後進行抽神經? 和患者說明當下醫師欲進行緊急處置與消炎的原因後，患者安心許多，會先按時吃藥觀察，並注意清潔。[院內追蹤] 1. 因為醫師沒有告知甚麼時候回診，也沒說明''可以回診的區間日期''，希望同仁能協助和醫師確認一下，並且先致電預約。 2. 病人晚上的時間都可配合，還請同仁今天幫忙回電病人唷!"
	}
}
```



## <a name="postAppointmentReminder"></a>上傳約診提醒資料

#### <a name="postARDefinition"></a>定義
約診提醒的作用是用來善意的提醒病患，其下次看診當天的報到時間、地點與看診時應注意的事項等資訊。

約診提醒可以透過 Dr. Right 的簡訊服務來發送。

所有資料皆依據與使用者約定方式處理。

#### <a name="postARMethod"></a>方法
Method: `POST`

URL: https://HOST/hospital/{hosp_id}/token/{token}/ap_reminder

#### <a name="postARParams"></a>參數
hosp_id 為該病歷資料所保有之診所 id，需要先行定義，可使用多種格式，例如健保署醫事代碼。

token 為先前取得的身分認證碼。

#### <a name="postARData"></a>上傳資料
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
		"special_reminder" : "請攜帶矯正費用 15,000 圓"
	},
	{
		"patient" : "林語文",
		"patient_id" : "000010221",
		"appointment_datetime" : "2021-08-13 20:00",
		"send_msg_datetime" : "2021-08-12 09:30",
		"doctor_name" : "黃清清",
		"special_reminder" : ""
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
		"id" : "dD54Dde8lgR420Hv46Rt2zoeRygh387Thd"
	},
	{
		"patient_id" : "000010221",
		"appointment_datetime" : "2021-08-13 20:00",
		"id" : "3Rtg63Jipdhi7IqaE41wPli9rFextR53Es"
	}
   ]
}
```









