# 플레이샵 양궁·사격 점수표

- 누구나 링크로 접속해 실시간 점수를 볼 수 있습니다.
- 비밀번호를 아는 사람만 점수를 입력할 수 있습니다.
- 페이지는 GitHub Pages에, 점수 데이터는 Firebase Firestore에 저장됩니다.

## Firebase 준비 (한 번만, 약 5분)

1. https://console.firebase.google.com 에서 **프로젝트 추가** → 이름 예: `playshop-score` → Google 애널리틱스는 꺼도 됩니다.
2. **빌드 > Firestore Database > 데이터베이스 만들기** → 위치 `asia-northeast3 (서울)` → **프로덕션 모드**로 시작.
3. Firestore의 **규칙** 탭에 `firestore.rules` 파일 내용을 붙여 넣고 **게시**.
4. **빌드 > Authentication > 시작하기** → 로그인 방법에서 **이메일/비밀번호** 사용 설정.
5. Authentication의 **사용자** 탭 → **사용자 추가**
   - 이메일: `playshop-scorer@example.com`
   - 비밀번호: 점수 입력자에게만 알려 줄 비밀번호
6. Authentication의 **설정 > 승인된 도메인**에 `wbhong79-ai.github.io` 추가.
7. **프로젝트 설정(톱니바퀴) > 내 앱 > 웹 앱 추가(</>)** → 표시되는 `firebaseConfig`의 `apiKey`, `authDomain`, `projectId`, `appId` 값을 `index.html` 상단 `FIREBASE_CONFIG`에 넣습니다.

처음 비밀번호로 입력 모드에 들어가면 기본 팀(줄리·주디·루크·댄팀, 3·3·3·2명)과 상금 규칙이 자동으로 만들어집니다.

## 비밀번호 바꾸기

Firebase 콘솔 > Authentication > 사용자에서 `playshop-scorer@example.com`의 비밀번호를 재설정하면 됩니다. 페이지 코드는 고칠 필요가 없습니다.
