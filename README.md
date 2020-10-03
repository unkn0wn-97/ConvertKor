# ConvertKor V2.5.1 - 한글 변환 플러그인

원본 제작자: RedMat
수정자: KR_WOLF#5912 = UNKNOWN#2214
도움: noname/RedMat

## ConvertKor 다운로드
[ConvertKor 다운로드](https://drive.google.com/file/d/1OjLArQbvYlda-2mbWQYNO7vAGNGPOFC_/view?usp=sharing, "download link")

## 필수 다운로드 플러그인 -   
https://umod.org/plugins/better-chat   
https://umod.org/plugins/better-chat-mute   

## 선택 다운로드 플러그인 -

**무료**   
https://umod.org/plugins/private-messages - 귓말 플러그인 입니다.   
https://umod.org/plugins/rustio-clans - 클랜 플러그인 입니다. (기능 적당한 버전)   
https://umod.org/plugins/clans - 클랜 플러그인 입니다. (기능 많은 버전)   
**유료**   
https://www.chaoscode.io/resources/clans-reborn.14/ - 클랜 플러그인 유료버전 (지리는 버전)   

## API - 

```
영어 -> 한글 변환
ConvertKor?.Call("GetConvertKor", message).ToString();

ex) message = ConvertKor?.Call("GetConvertKor", message).ToString();

플레이어가 한글 상태인지 영어 상태인지 확인합니다.

ConvertKor.Call("isConvertKor", player))

```
## 기능 -
```
1. 채팅을 한글로 변환해줍니다. ex) dkssudgktpdy -> 안녕하세요
2. 욕설 필터링 해줍니다. ex) 시발 -> ** (config 에서 수정가능합니다.)
  2.1 욕설 추가는 oxide/data 폴더 에 ConvertKor_ForbiddenWordData.json 파일에서 수정하시면 됩니다.
3. 욕설 감지 될 경우 -> 자동 채팅금지, 강퇴, 시간 밴, 영구 밴 할 수 있습니다. (config 에서 수정해야합니다.)
4. 경고 후 처리 기능
```

## 미래 계획 -
```
1. 자체 뮤트 기능
2. 자체 채팅 기능
3. 자동 업데이트 확인 기능
4. 코드 최적화
5. 확실한 언어 기능
```
## 콘피그(Config) -
```json
oxide/config 폴더 에 ConvertKor.json
{
  "1. 자동 처리 (0 - 비활성화 / 1 - 채팅금지 / 2 - 강퇴 / 3 - 시간 밴 / 4 - 영구 밴)": 0,
  "1. 채팅 금지 자동 처리 시간 설정 (s - 초 / m - 분 / h - 시간 / d - 일 / w - 주": "10m",
  "1. 시간 밴 시간 설정 (시간고정됨)": 1,
  "2. 경고 후 처리 (0 - 비활성화 / 1 - 활성화)": 0,
  "2. 경고 횟수": 5,
  "3. 한/영 GUI 토글 (true - 활성화 / false - 비활성화)": true,
  "4. 비속어 필터링 설정(시발 -> **)": "*",
  "5. 단어집 토글 (true - 활성화 / false - 비활성화)": true,
  "5.1. 단어집 추가": {
    "ㅋ": "킼",
    "ㅎ": "핳",
    "ㅇㅋ": "오키",
    "ㅂㅇ": "바이",
    "ㅎㅇ": "하이",
    "ㄷ": "덜",
    "ㄱ": "기억",
    "ㅂㄷ": "부들",
    "ㅜ": "T",
    "ㅠ": "T",
    "ㅈㅅ": "죄송",
    "ㅆㄹ": "쏘리",
    "ㄱㅊ": "괜츈",
    "ㄴㄴ": "노노",
    "ㅅㅇㄹ": "소오름",
    "ㅇㅅㅇ": "응슷응",
    "ㅇㅂㅇ": "응븝응",
    "ㅇ_ㅇ": "응_응"
  }
}
```
## 데이타(Data) -
```json
oxide/data 폴더 에 ConvertKor_PlayerData.json (건들지마세요!)
{
  "고유번호": {
    "WarnCount": 0,
    "Cooldown": 0,
    "KorMode": "KR",
    "UI": "활성화"
  },
}
oxide/data 폴더 에 ConvertKor_ForbiddenWordData.json (비속어 추가)
{
  "word": [
    "씨팔",
    "개새끼",
    "애미",
    "에미",
    "애비",
    "에비"
  ]
}
```
## 언어(Lang) -
```json
oxide/lang/en 폴더에 ConvertKor.json 
{
  "MuteReason": "욕설감지 되었습니다. {0} {1}",
  "KickReason": "{0} 님은 욕설 사용을 하여 강퇴 되었습니다.",
  "BanReason": "{0} 님은 욕설 사용을 하여 {1} 시간 밴 되었습니다.",
  "PBanReason": "{0} 님은 욕설을 사용하여 영구밴 되었습니다.",
  "Korean": "<color=lime>한</color>",
  "English": "<color=#00ffff>영</color>",
  "Prefix": "[<b><color=#00ff00>한글</color></b>]",
  "NoPermission": "<color=red>당신은 권한이 없습니다.</color>"
}
```

## 업데이트 정보 -
```
V2.5.2
1. 한글/영어 확인하는 API 확인 하던 도중 API 가 전혀 동작을 안하는것을 수정하였습니다.

V2.5.1
1. 실수로 OnPlayerInit Hook 을 안지운 버전 올렸네요..

V2.5.0
1. /pm, /c, /r 자동으로 한글로 변환 시켜줌. (RedMat 도와주심.)
2. 단어집이 추가됨. ex) ㅋ -> 킼 , ㅎ -> 핳 이런식
  2.1 콘피그에 단어집 추가됨. (ON/OFF 가능)
3. GUI 위치 변경됨.
  3.1 GUI 명령어 변경됨 /chatui
  3.2 GUI 콘피그 ON/OFF 체크함.
4. Umod API OnPlayerInit 이 더이상 사용되지않아서 OnPlayerConnected 로 변경됨.
5. 없다 할때 업ㅅ다 라고 표시되는 부분 수정됨.

V2.4.1
1. 관리자가 욕설 처리 대상 되는 부분 수정됨.
2. 플레이어가 GUI(한/영) 켜고 끄는 기능 추가됨. 명령어: /ui

V2.4.0
1. 콘피그 최적화 하였습니다.
  1.1 콘피그 GUI 부분 삭제.
  1.2 GUI 서버 자체에서 ON/OFF 기능 추가.
2. 경고 후 처리 기능 추가됨.
3. 데이터 최적화 진행함.
4. UI 작업 새로함.

V 2.3.3
1. 욕설 비속어 자동 처리 기능 추가
2. 언어 기능 추가됨.
3. 콘피그 추가됨.

V 2.3.0
레드멧님 제작/수정 하심.
```
**RedMat 에게 플러그인 수정 허락 받았습니다.**   
![CC](https://i.imgur.com/luutuST.png)
```
- 저작자표시-비영리 -
저작자를 밝히면 자유로운 이용이 가능하지만 영리목적으로 이용할 수 없습니다.
```
