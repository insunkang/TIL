## Android

### 설치

1. developer.android.com
2. navigationbar -> android 스튜디오 선택 (android스튜디오는 최신 버전을 받아주는것이 좋다)



### 특징

- 컴포넌트 기반
  Activity -> 화면단 하나
  Service
  ContentProvider -> 메시지 앱에서 전화 앱 서로 정보 공유 해주는것
  BroadCasetReceiver
- 리소스의 외부화 (안드로이드는 리소스를 전부 외부화 시키는데 성공)
  문자열 이미지
  화면
  외부파일


![image-20200324104900137](images/image-20200324104900137.png)

![image-20200324105530106](images/image-20200324105530106.png)

### 200325

![image-20200325093251030](images/image-20200325093251030.png)

![image-20200325093318799](images/image-20200325093318799.png)

LinearLayout 으로 변환

![image-20200325094041932](images/image-20200325094041932.png)

버튼이 생성되는 

- layout_width = view의 너비
- layout_height = view의 높이
- orientation = 배치방향
- id = 각 위젯을 식별할 수 있는 이름
  		btn
          txt
- margin : 주위 여백
- padding : 내부 컨텐츠와 border사이의 간격
- layout_weight : 여백을 해당 view의 사이즈로 포함
- layout_gravity : parent내부에서 view의 정렬     
- gravity : view내부에서의 정렬                    



![image-20200325094630969](images/image-20200325094630969.png)

match_parent하면 다 겹쳐짐 -> 부모 사이즈로 맞취때문에

![image-20200325094727591](images/image-20200325094727591.png)

wrap_content로 모두 바꿔주면 다시 돌아오는 것을 볼 수 있다.

