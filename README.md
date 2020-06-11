# Admixer integration guide.



This document is RTB integration specification for `DSP` that wish to buy Admixer’s inventories real time in order to run their ads on them.  
This document complies with the OpenRTB 2.3 specificatoin.

Therefore, this document does not cover details regarding BidRequest/Response.  
For more details on these, please check OpenRTB 2.3 specification via below link.

https://www.iab.com/wp-content/uploads/2015/06/OpenRTB-API-Specification-Version-2-3.pdf

If you have any question about this document, please reach out to admixer@nasmedia.co.kr.  
<br>

# 1. Bid Request Specification
## Object model

Object | Support | OpenRTB 2.3 Section for Reference | Extension
:--- | :---: | :---: | :---
BidRequest | O | 3.2.1 | X
Imp | O | 3.2.2 | X
Banner | O | 3.2.3 | X
Video | O | 3.2.4 | X
Native | O | 3.2.5 | X
Site | O | 3.2.6 | X
App | O | 3.2.7 | X
Publisher | O | 3.2.8 | X
Content | O | 3.2.9 | X
Producer | X | 3.2.10 | -
Device | O | 3.2.11 | X
Geo | O | 3.2.12 | X
User | O | 3.2.13 | O
Data | X | 3.2.14 | -
Segment | X | 3.2.15 | -
Regs | O | 3.2.16 | O
PMP | X | 3.2.17 | -
Deal | X | 3.2.18 | -
<br>

## Request sample

## Banner
	{
		"id": "0m1hqt5x",
		"imp": [{
			"id": "1",
			"bidfloor": 0.03,
			"bidfloorcur": "USD",
			"banner": {
				"w": 320,
				"h": 50,
				"btype": [1, 3, 4]
			}
		}],
		"app": {
			"id": "78e87y2f284vry62",
			"name": "com.test",
			"bundle": "com.test",
			"storeurl": "https://play.google.com/store/apps/details?id=com.test",
			"cat": ["IAB3"],
	"publisher": {
			        "id": "1234"
		         }
		},
		"device": {
			"ua": "Mozilla/5.0 (Linux; Android 4.4.4; Nexus 5 Build/KTU84P) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/33.0.0.0 Mobile Safari/537.36",
			"os": "android",
			"osv": "4.4.4",
			"model": "SHV-E160K",
			"ip": "123.145.167.189",
			"ifa": "f5edbc38-2614-4470-927c-f182fc003411"
		},
		"regs": {
			"ext": {
				"gdpr": 0
			}
		}
	}
<br>

## Video
	{
		"id": "0m1hqt5x",
		"imp": [{
			"id": "1",
			"bidfloor": 0.03,
			"video": {
				"w": 640,
				"h": 480,
				"minduration": 5,
				"maxduration": 30,
				"api": [1, 2],
				"protocols": [2, 3],
				"mimes": ["video/x-flv", "video/mp4", "application/x-shockwave-flash", "application/javascript"],
				"battr": [13, 14]
			}
		}],
		"app": {
			"id": "78e87y2f284vry62",
			"name": "test app",
			"bundle": "com.app.test",
			"storeurl": "http://test.test",
			"cat": ["IAB3"],
			"content": {
				"id": "abcde",
				"episode": "test episode",
				"series": "test series",
				"season": "test season",
				"cat": ["IAB3"]
			}
		},
		"device": {
			"ua": "Mozilla/5.0 (Linux; Android 4.4.4; Nexus 5 Build/KTU84P) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/33.0.0.0 Mobile Safari/537.36",
			"os": "android",
			"osv": "4.4.4",
			"model": "SHV-E160K",
			"ip": "123.145.167.189",
			"ifa": "f5edbc38-2614-4470-927c-f182fc003411"
		},
		"regs": {
			"ext": {
				"gdpr": 0
			}
		}
	}
<br>

## Native
	{ 
		"id": "0m1hqt5x", 
		"imp": [{ 
			"id": "1001-2000-3000-4000", 
			"bidfloor": 0.03, 
			"native": { 
				"request": "{\"native\":{\"ver\":\"1.2\",\"assets\":[ ... ]}}", 
				"ver": "1.2", 
				"api": [3], 
				"battr": [13, 14] 
			} 
		}], 
		"app": { 
			"id": "78e87y2f284vry62", 
			"name": "test app", 
			"bundle": "com.app.test", 
			"storeurl": "http://test.test", 
			"cat": ["IAB3"] 
		}, 
		"device": { 
			"ua": "Mozilla/5.0 (Linux; Android 4.4.4; Nexus 5 Build/KTU84P) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/33.0.0.0 Mobile Safari/537.36", 
			"os": "android", 
			"osv": "4.4.4", 
			"model": "SHV-E160K", 
			"ip": "123.145.167.189", 
			"ifa": "f5edbc38-2614-4470-927c-f182fc003411" 
		}, 
		"regs": { 
			"ext": { 
				"gdpr": 0 
			} 
		} 
	} 
<br>

# 2. Bid Response Specification
## Object model

Object | Support | OpenRTB 2.3 Section for Reference | Extension
:--- | :---: | :---: | :---
BidResponse | O | 4.2.1 | X
SeatBid | O | 4.2.2 | X
Bid | O | 4.2.3 | X
<br>

## Object Specifications

- Object : BidResponse

Field name | Support
:--- | :---
id | O (Mandatory)
seatbid | O
bidid | O
cur | O (USD only)
customdata | X
nbr | X
ext | X
<br>

- Object : SeatBid

Field name | Support
:--- | :---
bid | O (Mandatory)
seat | O
group | X
ext | X
<br>

- Object : Bid

Field name | Support
:--- | :---
id | O (Mandatory)
impid | O (Mandatory)
price | O (Mandatory)
adid | O
nurl | X
adm | O (Mandatory), Format: HTML<br>Win notice URL must be included within HTML.
adomain | O (Mandatory)
bundle | O (Mandatory)
iurl | O (Mandatory)
cid | O (Mandatory)
crid | O (Mandatory)
cat | O
attr | O
dealid | X
h | O
w | O
ext | X
<br>

## Response sample

## Banner
	{
		"id": "1234567890",
		"bidid": "abc1123",
		"cur": "USD",
		"seatbid": [{
			"seat": "512",
			"bid": [{
				"id": "1",
				"impid": "1",
				"price": 9.43,
				"adomain": ["aaa.com"],
				"bundle": "com.test",
				"iurl": "http://test.com/image/aaa.jpg",
				"cid": "100",
				"crid": "1234",
				"adm": "<div style=\"width:100%;height:100%;text-align:center;\"><a href=\"http://test.admixer.co.kr/click\" target=\"_top\" style=\"text-decoration:none;\"><img id=\"ad\" src=\"http://test.admixer.co.kr/image.jpg\" style=\"width:320px;height:50px;border:0px;\"/></a><img src=\"http://test.admixer.co.kr/winnotice?impid=102&price=${AUCTION_PRICE}\" style=\"width:1px;height:1px;display:none;\" /></div>",
				"attr": [1, 2, 3, 4, 5, 6, 7, 12]
			}]
		}]
	}
<br>

## Video
	{
		"id": "0m1hqt5x",
		"bidid": "abc1123",
		"cur": "USD",
		"seatbid": [{
			"seat": "512",
			"bid": [{
				"id": "adxb_20151203171854390422024850",
				"impid": "1",
				"price": 1.2,
				"adomain": ["aaa.com"],
				"bundle": "com.test",
				"cid": "100",
				"crid": "1234",
				"adm": "<?xml version=\"1.0\" encoding=\"UTF-8\"?><VAST version=\"2.0\"></VAST>"
			}]
		}]
	}
 
<br>

## Native
	{
		"id": "0m1hqt5x",
		"bidid": "abc1123",
		"cur": "USD",
		"seatbid": [{
			"seat": "512",
			"bid": [{
				"id": "adxb_20151203171854390422024850",
				"impid": "1",
				"price": 1.2,
				"adomain": ["aaa.com"],
				"bundle": "com.test",
				"iurl": "http://test.com/image/aaa.jpg",
				"cid": "100",
				"crid": "1234",
				"adm": "{\"native\":{\"ver\":\"1.0\",\"link\":{ ... }, \"imptrackers\":[ ... ],\"assets\":[ ... ]}}"
			}]
		}]
	}
<br>

## Macro Replacement

Macro | Explanation | Support
:--- | :---: | :---
${AUCTION_ID} | BidRequest.id | O
${AUCTION_BID_ID} | BidResponse.id | O
${AUCTION_IMP_ID} | win Imp.id | O
${AUCTION_SEAT_ID} | win SeatBid.seat | O
${AUCTION_AD_ID} | Bid.adid | O
${AUCTION_PRICE} | win Price | O
${AUCTION_PRICE:B64} | win Price (Base64 encoding) | O
${AUCTION_CURRENCY} | Currency of win price | O
<br>

## Win notice

Method | Explanation
:--- | :---
Client-to-Server | Win notice URL must be included within Bid.adm.<br>After the Macro Replacement process of the URL, it gets sent to the client.<br>-> Calls for Win notice URL during the client’s ad HTML loading process.
