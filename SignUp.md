# Boost Sign Up

네이버 부스트 코스 프로젝트 B - 회원 가입
많은 애플리케이션에서 활용해 볼 수 있는 회원가입 절차를 구현해 볼 수 있습니다. 
물론 모든 애플리케이션에서 활용하기엔 조금 복잡한 절차들이지만 내비게이션 인터페이스와 모달을 이해할 수 있습니다.
여러 화면에서 공유해야 하는 데이터를 어떻게 관리할 수 있을지 고민해 볼 수도 있습니다. 
또, 디자인 패턴을 작게나마 실질적으로 구현해 봄으로써 몇몇 디자인 패턴에 대한 이해를 증진할 수 있습니다.

<u></u>

# 기능
## 화면 1 - 로그인 화면

- Password TextField는 마스킹이 되어야 한다.

## 화면 2 - 회원가입 화면(기본정보)

- 프로필 이미지의 비율은 1:1이다.
- 프로필 이미지는 원본 비율을 유지해야 한다.
- 세 개의 TextField는 여백이 동일하다(균등 분배).
- 패스워드와 패스워드 체크 TextField는 마스킹이 되어야 한다.
- 중간 자기소개 TextField는 상하 View를 배치한 뒤 빈 여백을 모두 채운다.
- 자기소개 TextField는 내부 패딩이 존재하며 왼쪽 위부터 글자가 작성된다.
- 다음 버튼은 기본적으론 비활성화이며 모든 정보가 입력되었고 패스워드가 일치하면 활성화된다.

## 화면 3 - 회원가입 화면(부가정보)

- 전화번호는 숫자 키패드가 나온다.
- 생년월일을 선택할 때마다 즉시 Label에 반영된다.
- 이전 버튼을 누르면 정보가 유지된 채 화면 2로 넘어가야 한다.
- 화면 2에서 화면 3으로 재진입하면 기존 입력한 정보가 보여야 한다.
- 취소 버튼을 누르면 모든 정보가 지워지고 화면 1로 돌아가야 한다.
- 가입 버튼을 누르면 화면1로 돌아가고 ID가 채워져야 한다.

<u></u>

# 작업 기록

## 2021-11-24

- 로그인 화면
  - [추가] 타이틀 이미지 추가
  - [추가] id, password 텍스트 필드 추가
  - [추가] Sign in, Sign up 버튼 추가
  - [추가] 오토 레이아웃 적용

- 회원가입 화면 - 기본 정보
  - [추가] 프로필 이미지 추가
  - [추가] 정보 입력 텍스트 필드 추가
  - [추가] 취소, 다음 버튼 추가
  - [추가] 오토 레이아웃 적용
  - [예정] 정보 입력 텍스트 필드 Padding 추가 예정

## 2021-11-26

- 로그인 화면
    - [추가] 화면 밖 터치 시 키보드 내려가게 처리
    - [추가] viewDidAppear()마다 Id 설정
    
- 회원가입 화면 - 기본 정보
    - [추가] 취소 버튼 액션 추가
    - [추가] 프로필 이미지 누르면 사진 선택 기능 추가
    - [추가] 텍스트 필드 입력마다 UserInfomation 데이터 삽입 추가
    - [추가] 비밀번호와 비밀번호 체크 동일한지 비교 로직 추가
    - [추가] 다음 버튼 활성화/비활성화 추가
    - [추가] 입력 정보 싱글톤 객체에 대입
    - [이슈] Introduction 글자가 없는데 한 번 더 지워지는 액션이 됨. -> 다음 버튼 비활성화 안 됨

- 회원가입 화면 - 부가 정보
    - [추가] 전화번호 텍스트 필드 추가
    - [추가] 생년월일 레이블, DatePicker 추가
    - [추가] 버튼 세 개 추가
    - [추가] 이전 버튼 액션 추가
    - [추가] 취소 버튼 액션 추가
    - [추가] Date Picker 값 Label에 대입 추가
    - [추기] 취소, 이전 액션 추가
    - [추가] 가입 활성화/비활성화 추가
    - [추가] 입력 정보 싱글톤 객체에 대입

## 2021-11-27

- 로그인 화면
    - [수정] id 적용이 즉각 반영되도록 수정(viewDidAppear() -> viewWillAppear()로 수정)

- 회원가입 화면 - 기본 정보
    - [수정] Introduction 첫 글자 이슈 수정 
        - old Text를 가지고 있어서 발생한 이슈였음.
        - textViewDidChange()로 수정.

## 2021-12-03

- 공통
    - 코드 리뷰 피드백 적용 
    - [수정] 네비게이션 컨트롤러 적용
    
- 로그인 화면
    - [수정] StackView 제약 추가 -> Warning 수정
    - [추가] unwind Segue 추가
    
- 회원가입(기본정보)
    - [수정] tabGestureRecognizer를 스토리보드에서 적용
    - [수정] 이미지뷰에 대한 설정을 스토리보드에서 적용
    - [수정] nextButton.isEnabled를 스토리보드에서 적용
    - [수정] UIImagePickerControllerDelegate를 extension으로 수정

- 회원가입(부가정보)
    - [수정] Birth Label의 trailing 제약을 SuperView에서 SafeArea로 수정
    - [수정] 이전 버튼을 dismiss -> pop으로 수정
    - [수정] unwind Segue를 이용해 Login ViewController로 이동하도록 수정 
