# 그누보드 6 (가칭)

## 목표

1. 현재 그누보드와 같은 구조를 유지하지만, 데이타베이스 일부 테이블에 Relationship ID를 넣어서 ORM을 사용할 수 있게 한다.
2. `me_code`, `wr_comment_reply`와 같이 문자로 Depth를 만든 것을 **parent** **child** 구조로 변경함.
3. `image`와 `icon`을 `g5_member field`에 추가 필요함
4. 게시판 테이블에 있는 category도 별도의 테이블로 사용함.
5. Tag 테이블도 추가

## 백엔드에서 필요한 것

1. JWT토큰
2. 리플리시 토큰
3. 파일 업로드
4. 이메일전송.
5. 2FA
6. Push notification
7. Chatting
8. SMS 전송/인증

## REST API

### 게시판 읽어오기

1. GET /api/v1/[board]
2. GET /api/v1/[board]/[id]
3. GET /api/v1/[board]/[id]/comments
4. GET /api/v1/[board]/[id]/comments/[c_id]
5. GET /api/v1/[board]/[id]/goods
6. GET /api/v1/[board]/[id]/nogoods

```
{
  "post": {
    "wrId": 1,
    "wrNum": -1,
    "wrReply": "",
    "wrParent": 1,
    "wrIsComment": 0,
    "wrComment": 8,
    "wrCommentReply": "",
    "caName": "잡담",
    "wrOption": [
      "html1"
    ],
    "wrSubject": "flask(플라스크) 서평 이벤트에 당첨되었어요",
    "wrContent": "<p><img src=\"https://yc5.lavuebd.com/data/editor/2012/a8810e5e7fbd5907e2be8a5b60fd3e1c_1608708239_1957.jpg\" title=\"a8810e5e7fbd5907e2be8a5b60fd3e1c_1608708239_1957.jpg\" alt=\"a8810e5e7fbd5907e2be8a5b60fd3e1c_1608708239_1957.jpg\"></p><p style=\"color:rgb(34,34,34);font-family:'Apple SD Gothic Neo', 'Malgun Gothic', '맑은 고딕', sans-serif;font-size:14px;\">점프 투 파이썬의 저자님이 후속 책을 쓰셨고요</p><p style=\"color:rgb(34,34,34);font-family:'Apple SD Gothic Neo', 'Malgun Gothic', '맑은 고딕', sans-serif;font-size:14px;\"><a href=\"https://wikidocs.net/book/4542\" target=\"_blank\" style=\"color:rgb(7,130,193);\" rel=\"nofollow noreferrer noopener\">https://wikidocs.net/book/4542</a></p><p style=\"color:rgb(34,34,34);font-family:'Apple SD Gothic Neo', 'Malgun Gothic', '맑은 고딕', sans-serif;font-size:14px;\">위 링크에서도 책과 동일한 내용이 있습니다.</p><p style=\"color:rgb(34,34,34);font-family:'Apple SD Gothic Neo', 'Malgun Gothic', '맑은 고딕', sans-serif;font-size:14px;\"> </p><p style=\"color:rgb(34,34,34);font-family:'Apple SD Gothic Neo', 'Malgun Gothic', '맑은 고딕', sans-serif;font-size:14px;\"> </p><p style=\"color:rgb(34,34,34);font-family:'Apple SD Gothic Neo', 'Malgun Gothic', '맑은 고딕', sans-serif;font-size:14px;\">얼마전 <a href=\"https://sir.kr/main/member/?mb_id=box2\" class=\"mention_user_info\" target=\"_blank\" style=\"color:rgb(7,130,193);font-weight:bold;\" rel=\"nofollow noreferrer noopener\">@박스2</a> 님께서도 </p><p style=\"color:rgb(34,34,34);font-family:'Apple SD Gothic Neo', 'Malgun Gothic', '맑은 고딕', sans-serif;font-size:14px;\">구입하신 책입니다.</p><p style=\"color:rgb(34,34,34);font-family:'Apple SD Gothic Neo', 'Malgun Gothic', '맑은 고딕', sans-serif;font-size:14px;\"> </p><p style=\"color:rgb(34,34,34);font-family:'Apple SD Gothic Neo', 'Malgun Gothic', '맑은 고딕', sans-serif;font-size:14px;\">12월 14일 이후부터 읽기 가능할것 같습니다.</p><p style=\"color:rgb(34,34,34);font-family:'Apple SD Gothic Neo', 'Malgun Gothic', '맑은 고딕', sans-serif;font-size:14px;\"> </p><p style=\"color:rgb(34,34,34);font-family:'Apple SD Gothic Neo', 'Malgun Gothic', '맑은 고딕', sans-serif;font-size:14px;\">서평은 처음인데 </p><p style=\"color:rgb(34,34,34);font-family:'Apple SD Gothic Neo', 'Malgun Gothic', '맑은 고딕', sans-serif;font-size:14px;\">시작전에 인증글 남기고 갑니다.</p><p style=\"color:rgb(34,34,34);font-family:'Apple SD Gothic Neo', 'Malgun Gothic', '맑은 고딕', sans-serif;font-size:14px;\"> </p><p style=\"color:rgb(34,34,34);font-family:'Apple SD Gothic Neo', 'Malgun Gothic', '맑은 고딕', sans-serif;font-size:14px;\">안녕히 주무세요.</p><p><br></p>",
    "wrSeoTitle": "flask플라스크-서평-이벤트에-당첨되었어요",
    "wrHit": 27,
    "wrGood": 4,
    "wrNogood": 2,
    "mbId": "sundoforce",
    "wrPassword": "",
    "wrName": "선구자",
    "wrEmail": "*** 개인정보보호를 위한 이메일주소 노출방지 ***",
    "wrHomepage": "",
    "wrDatetime": "2020-12-23T16:24:23.000Z",
    "wrFile": 2,
    "wrLast": "2020-12-23 16:29:14",
    "wrIp": "127.0.0.1",
    "wrFacebookUser": "",
    "wrTwitterUser": "",
    "wrLinks": [
      {
        "link": "https://wikidocs.net/book/4542",
        "hit": 1
      },
      {
        "link": "https://www.apachezone.com/free/6968",
        "hit": 0
      }
    ],
    "extras": {
      "wr_1": "",
      "wr_2": "",
      "wr_3": "",
      "wr_4": "",
      "wr_5": "",
      "wr_6": "",
      "wr_7": "",
      "wr_8": "",
      "wr_9": "",
      "wr_10": ""
    },
    "wrFiles": [
      {
        "boTable": "free",
        "wrId": 1,
        "bfNo": 0,
        "bfSource": "test.txt",
        "bfFile": "800597403_jcHK9GVR_5c4f0ace2c37d561a79ab8641bb9a46d1fd47ada.txt",
        "bfDownload": 0,
        "bfContent": "",
        "bfFileurl": "",
        "bfThumburl": "",
        "bfStorage": "",
        "bfFilesize": 146,
        "bfWidth": 0,
        "bfHeight": 0,
        "bfType": 0,
        "bfDatetime": "2021-03-21T11:29:49.000Z"
      },
      {
        "boTable": "free",
        "wrId": 1,
        "bfNo": 1,
        "bfSource": "test.csv",
        "bfFile": "800597403_KLjHBZ0o_75b19924e8f19d6d11600e22f7ed27e8b50d81d1.csv",
        "bfDownload": 0,
        "bfContent": "",
        "bfFileurl": "",
        "bfThumburl": "",
        "bfStorage": "",
        "bfFilesize": 149,
        "bfWidth": 0,
        "bfHeight": 0,
        "bfType": 0,
        "bfDatetime": "2021-03-21T11:29:49.000Z"
      }
    ]
  }
}
```

### 멤버 관련
1. /api/v1/member/[mbId]/points
2. /api/v1/member/[mbId]/scraps
3. /api/v1/member/[mbId]/memos
