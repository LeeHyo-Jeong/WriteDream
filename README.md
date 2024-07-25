## 바다, 저거.. 꾸물..
> 밤 동안의 꿈을 다양한 방식으로 기록할 수 있는 웹사이트

### 사이트 소개💭

여러분 혹시 꿈 자주 꾸시나요? 저는 늘 꿈의 내용이 너무 재밌고 신박해서, ‘언젠간 이야기거리나 글감이 되겠다!’ 싶어서 꿈 일기를 적는 편입니다.
하지만 일어나자마자 졸린 채로 음성인식으로 기록을 하면 제목처럼 무슨 말인지 모를 글이 완성되고 말죠..
‘바다.. 저거.. 꾸물..? 꾸물대는 저게 바다라는 건가? 꿈에서 해변가에 놀러갔나?’싶게, 온전하지 못한 기록을 하면 나중에 다시 봤을 때 잘 기억이 나지 않을 거예요.
그런 분들을 위해, ‘꾸물대는 저 바다’에 ‘꿈을’ ‘받아서’ ‘적을’ 수 있도록 한 웹사이트가 바로 저희가 개발한 사이트입니다.

<img width="1280" alt="notion_cover" src="https://github.com/user-attachments/assets/c38d4113-06cf-41fd-b366-3857440f62fb">

### ‘바다, 저거.. 꾸물..’은…🥱

1. 로그인 후 꿈의 바다로 들어가는 물이 차오르는 ‘메인 페이지’
2. 월별로 정리된 꿈 일기를 바다 생물로 볼 수 있는 ‘바다 페이지’
3. 새로운 일기를 작성하러 갈 수 있는 ‘고래 뱃속 페이지’
4. 글, 그림, 녹음 등의 방식으로 일기를 작성할 수 있는 ‘작성 페이지’
로 이루어져 있습니다.

### 개발 환경💻

- React
- MongoDB
- Node.js
- AWS EC2
- Docker
- Figma, Adobe Illustrator

## Details

### 1. 메인 🌜

- 로그인 후 꿈의 바다로 들어가는 물이 차오르는 페이지

![제목 없는 동영상 - Clipchamp로 제작](https://github.com/user-attachments/assets/aaf71436-fea4-4211-8867-9204c69efcbd)

- 회원가입: 새로운 아이디와 비밀번호를 입력하고 회원가입 버튼을 누르면 닉네임을 입력하는 창이 뜹니다. 완료를 누르면 회원가입이 완료됩니다.
- 로그인: 기존의 아이디와 비밀번호를 입력하고 로그인 버튼을 누르면 물이 차오르며 다음 페이지로 전환됩니다.
- 회원가입과 로그인 및 모든 서버에 대한 요청은 jwt 토큰 방식을 이용합니다. 회원가입시 유저에게 access token을 발급합니다. 로그인 한 유저는 이 access token을 이용해 서버에 필요한 정보를 요청합니다. 백엔드는 프론트엔드의 모든 요청을 verifyToken 미들웨어를 거쳐 토큰을 점검해 유효한 토큰일 때만 프론트의 요청을 처리합니다.
- 파도 애니메이션: wavegroup 인스턴스를 이용하여 여러 파도가 끊임없이 칠 수 있도록 연출하였습니다. wavegroup을 만들기 위해서는 point.js와 wave.js를 사용하는데, 위아래로 움직이는 점들을 찍고 그들을 곡선으로 잇는 방식으로 파도를 그리는 것입니다.
    - 김종민 엔지니어님의 다음 영상을 많이 참고하였습니다. (https://www.youtube.com/watch?v=LLfhY4eVwDY&t=2s)
- 물 차오르는 애니메이션: login에 성공하면 centerY의 값이 변화하면서 물이 차오르도록 하였습니다.

### 2. 바다 🌊

- 월별로 정리된 꿈 일기를 바다 생물로 볼 수 있는 페이지

![제목 없는 동영상 - Clipchamp로 제작 (1)](https://github.com/user-attachments/assets/eaba51b8-1d5f-4f01-9037-fd9c33b92af2)

- 꿈의 바다
    - 일기 작성시 기록한 날짜에 맞추어 월별로 정리된 꿈의 바다를 보여줍니다.
    - ‘<’와 ‘>’ 버튼을 눌러 앞뒤 달로 이동할 수 있습니다.
    - 바다 생물들을 움직일 수 있습니다.
- 바다 생물
    - 해파리는 글로 작성한 일기, 물고기는 그림 일기, 해초는 음성 일기를 의미합니다.
    - 드래그하여 위치를 옮길 수 있고, 우클릭으로 삭제할 수 있고, 확대 및 축소도 가능합니다.
    - 더블클릭하여 일기를 열람할 수 있습니다. 생물 하나 당 일기 하나가 일대일대응입니다.
- footer의 버튼을 눌러 새로운 작성을 위한 뱃속 페이지로 전환할 수 있습니다.
    - 입 열고 닫는 애니메이션은 좋은 꿈과 나쁜 꿈을 고래가 모두 삼켜준다는 의미와, 고래의 뱃속 페이지로 일기를 작성하러 가는 전환의 의미가 있습니다.
    - css로 곡선과 직선을 만들고 컴포넌트에서 애니메이션을 제어하였고, 칠을 위해 svg 요소 내에 clipPath와 mask를 이용하여 곡선 사이의 공간을 투명하게 유지하도록 하였습니다.
    - Ocean에서 다른 페이지로 넘어갈 때 늘 입은 닫히지만, Belly로 갈 때에만 다시 입이 열리도록 하기 위해서 location.state.fromOcean을 이용하여 animateOpen의 작동 여부를 결정하도록 하였습니다.
  

### 3. 뱃속 🐳

- 새로운 일기를 작성하러 갈 수 있는 고래 뱃속
- 우리 피노키오는 이제는 거짓말을 하지 않는 아이가 되었기 때문에, 솔직하게 얘기할 수 있는 일기를 적기로 결심합니다🫠

![제목 없는 동영상 - Clipchamp로 제작 (2)](https://github.com/user-attachments/assets/5012e3a4-ce86-456d-85a5-07261369680b)

- 닉네임: 제페토 할아버지께서 회원가입시 입력한 이름으로 어떤 꿈을 꿨냐고 물어봐주십니다.
    - 그래서 위 영상에는 효정아, 이 영상에서는 싱송아, 라고 불러주십니다!!😳
- 일기 작성: 세 가지 방식으로 가능합니다.
    - 글 작성📝, 그림 그리기🎨, 녹음🎙️이 가능합니다.
    - 작성 방식을 선택하면 일기장의 배경 색을 정할 수 있는 박스들이 등장합니다.
    - 박스의 빈 공간을 클릭하여 다시 접을 수도 있습니다.
- 박스: click을 통해 색상에 대한 정보를 담아서 작성페이지로 넘어갈 수 있는 item들을 담는 container를, open의 여부에 따라서 다른 위치에 보이도록 만들고, 그 상태들을 부드럽게 이어줄 수 있도록 구현하였습니다.
  

### 4. 작성 ✍️

- 글, 그림, 녹음 등의 방식으로 일기를 작성할 수 있는 페이지
- 날짜를 선택하고 제목을 입력하는 칸은 모든 작성 페이지에 기본적으로 존재합니다.
- 작성이 완료되면 다시 바다 페이지로 이동하고, 일기에 대응하는 바다 생물이 추가됩니다.
![스크린샷 2024-07-25 164910](https://github.com/user-attachments/assets/96a50020-0e4b-4658-ae49-4f2c5a7033a0)
- 글 작성: 꿈의 내용을 작성할 수 있습니다. 체크를 누르면 저장됩니다.
![스크린샷 2024-07-25 164930](https://github.com/user-attachments/assets/29c53b3b-a1c3-45c7-90f9-a4d15277c514)
- 그림 그리기: 펜의 굵기, 색깔을 조정할 수 있고, 지우기 버튼이나 채우기 버튼을 사용할 수 있습니다. 그림 완성을 누른 후 체크를 누르면 저장됩니다.
![스크린샷 2024-07-25 164950](https://github.com/user-attachments/assets/c1ef5b70-9463-417d-a099-4aa460e46eb8)
- 녹음: 재생버튼으로 녹음을 재시작, 일시정지로 중지, 정지 버튼으로 마무리를 할 수 있습니다. 다시 들어볼 수 있는 바가 등장하고, 체크를 누르면 녹음된 음성 파일이 백엔드에서 파일을 업로드를 처리하는 multer 미들웨어를 거쳐  서버에 저장됩니다.


### 5. API 명세서 📄

<details>
<summary>Schema</summary>
  
  ### User
  
  | 이름 | 타입 |
  | --- | --- |
  | userId | number |
  | password | number |
  | diaries | Diary |
  | nickname | string |
  
  ### Diary
  
  | 이름 | 타입 |
  | --- | --- |
  | title | string |
  | contents | string |
  | date | Date |
  | audio | string |
  | image | string |
  | userObjectId | Object |
  | background | string |
  | type | string |
</details>

<details>
<summary>API</summary>

**서버에 대한 요청과 응답은 jwt token 방식을 이용합니다. 프론트에서는 요청 헤더에 다음을 포함해야 합니다.**

```jsx
headers: {
Authorization: `Bearer ${accessToken}`
}
```
**모든 요청에 대해 verifyToken 미들웨어를 거쳐 사용자가 유효한 토큰을 보유한 사용자인지 판단 후 응답합니다.**

- 회원가입
**POST**
`BASE_URL:4000/auth/register`

- 로그인
**POST**
`BASE_URL:4000/auth/login`

- 메인
**GET**
`API_URL:4000/diaries` 

- 일기
**GET, POST, PUT, DELETE**
`BASE_URL:4000/diary` 

- 월별로 일기 불러오기
**GET**
`BASE_URL:4000/diary/${selectedYear}/${selectedMonth}`

- 물고기 눌렀을 때 해당 다이어리 불러오기
**GET**
`BASE_URL:4000/diary/${type}/${diaryId}`

- 이미지 서버에 업로드
**POST**
`BASE_URL:4000/upload`
    
- 유저 정보 얻어오기
**GET**
`BASE_URL:4000/auth/user`

</details>

## 마무리🌠

이렇듯 ‘바다, 저거.. 꾸물..’은 꾼 꿈들을 월별로 나뉜 꿈의 바다에 기록하고, 그 꿈을 모두 삼켜주는 고래 뱃속에서 진실된 일기들을 작성할 수 있는 웹사이트입니다. 꾸물대는 바다에 꿈을 받아 적어보세요😉 감사합니다🫧
![notion_fin](https://github.com/user-attachments/assets/41463bc6-74f8-42af-af64-948b7cc8ac61)

## 제작자

> 개발기간: 1주
<br/><br/>
> 개발인원: 2명

|                                   신서원                                   |                                    이효정                                    |
|:-----------------------------------------------------------------------:|:-------------------------------------------------------------------------:|
| <img src = "https://avatars.githubusercontent.com/sswilove1" width=150px> | <img src = "https://avatars.githubusercontent.com/LeeHyo-Jeong" width=150px> |
|                 [@sswilove1](https://github.com/sswilove1)                  |                [@LeeHyo-Jeong](https://github.com/LeeHyo-Jeong)                 |

