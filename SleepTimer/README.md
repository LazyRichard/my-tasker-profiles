# Tasker를 이용한 취침 타이머

## 소개

<img src="https://user-images.githubusercontent.com/11005424/28620225-fd9a6a10-7246-11e7-8162-fc8d90213a55.png" width="1000">

유투브 앱의 경우에는 충전 상태가 변하게 되면 영상이 자동으로 일시정지 되기 때문에, 충전기를 꼽아두고 자면 다음날 아침 휴대폰 화면은 꺼져 있습니다. 하지만 트위치와 같은 앱의 경우에는 전혀 개의치 않기 때문에 아침 까지 화면이 켜져 있습니다. 이에 불편함을 느껴 어떻게 하면 이 사태를 해결할 수 있나 고민하던차에 쓰려고 샀지만 전혀 쓰지 못하고 있던 Tasker을 이용하여 이론상 모든 앱에 적용가능한 취침 타이머를 만들어보았습니다. 아직 완벽하게 동작하는 것은 아니기 때문에 혹시나 이걸 보고 혹해서 Tasker나 AutoInput앱을 구매하는 불상사는 없었으면 좋겠습니다.

### 특징

* 무료인듯 하지만 Tasker가 필요하므로 돈이 들어간다!
* 거의 모든 앱에 적용 가능하다.
* 취침 타이머를 적용하기로 한 앱간 타이머가 공유된다. (예. 유투브 앱에서 30분 취침 타이머를 실행한 후, 트위치 앱으로 넘어가도 취침 타이머는 계속 동작함)

## 주의사항

* 초단위 타이머는 제대로 동작하지 않을 가능성이 높습니다. 최소 1분 이상을 권장합니다.
* 현재 제가 Scene을 잘 다루지 못하는 관계로 변경한 값들이 제대로 반영되지 않을 수 있습니다. 체크박스의 경우에는 한 두번 눌러주면 원하는 값으로 적용됩니다.
* 꽤 많은 테스트들이 돌아가게 되고 알림을 갱신하는 등의 지속적인 동작을 수행하므로 배터리 사용량이 높을 수 있습니다. 충전기를 꼽고 사용하길 권장드립니다.

## 필요

Tasker를 제외하면 최대한 무료 앱을 사용할 수 있도록 구성했습니다. 다만 현재 실행중인 어플리케이션의 패키지 정보를 얻어오는데 있어, TouchTask 앱의 경우에는 패키지 정보를 제공해주지 않기 때문에 Java 코드를 이용하여 얻어오고 있습니다. 알고리즘상의 문제로 인하여 이 부분에서 체감상 10 ~ 15초의 시간이 소요됩니다. AutoInput는 자체적으로 패키지 정보를 리턴해주기 때문에 이러한 부분에서 속도 향상이 있습니다.

* (필수)Tasker - 유료, 2.99$, [Play Store](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm&hl=ko)
* (필수)TouchTask - 무료, [Play Store](https://play.google.com/store/apps/details?id=com.balda.touchtask&hl=ko)
* (선택)AutoInput - 유료, [Play Store](https://play.google.com/store/apps/details?id=com.joaomgcd.autoinput&hl=ko)

## 설치법

[다운로드 링크](https://github.com/LazyRichard/my-tasker-profiles/blob/master/SleepTimer/SleepTimer.prj.xml)

1. 다운받은 파일을 내장메모리/Tasker/Project 폴더에 저장합니다.

2. Tasker를 실행시키고, Preference에서 Beginner Mode에 체크를 해제합니다.

<img src="https://user-images.githubusercontent.com/11005424/28619481-990db7bc-7243-11e7-9939-f9bdbc21ed5d.png" width="500">

3. Tasker 하단에 집모양 버튼이 있는데 이를 클릭한 후, Import 메뉴를 이용해 저장한 프로젝트를 등록합니다.

<img src="https://user-images.githubusercontent.com/11005424/28619510-b3ed67b2-7243-11e7-8b80-f88fbcf3b301.png" width="500">

4. 하단에 시계 모양의 아이콘이 생겼으면 정상적으로 적용 된 것입니다.

<img src="https://user-images.githubusercontent.com/11005424/28619505-b3cd1cc8-7243-11e7-818c-e88293cf3189.png" width="250">

### AutoInput 사용자 전용

5. 유투브(혹은 타이머가 적용된 앱)를 실행시켜 프로그램 최초 설정을 진행합니다.

<img src="https://user-images.githubusercontent.com/11005424/28619509-b3e004dc-7243-11e7-858d-4ea5f0bbe498.png" width="250">

6. Tasker 하단에 시계 모양 버튼을 클릭한 후, VARS 탭으로 이동합니다.

<img src="https://user-images.githubusercontent.com/11005424/28619512-b3f1f372-7243-11e7-8ae2-58ebf036491f.png" width="250">

7. %ForegroundPkgNameTask를 클릭한 후, getForegroundAppPkgName를 getForegroundAppPkgNameFast로 변경합니다.

<img src="https://user-images.githubusercontent.com/11005424/28619511-b3f1c488-7243-11e7-82c4-5fdb6f1e4ded.png" width="500">

8. Tasker 우측 상단에 체크 표시를 눌러 설정을 적용합니다.

<img src="https://user-images.githubusercontent.com/11005424/28619514-b3feec12-7243-11e7-8c15-d437e84b35bf.png" width="250">

## 사용법

### 취침 타이머 적용 앱 설정

1. Tasker를 실행시키고, 하단에 시계 모양의 선택한 뒤, Profiles 탭에 Sleep Timer Main 항목 조건을 선택합니다.

<img src="https://user-images.githubusercontent.com/11005424/28619513-b3fe9686-7243-11e7-9ed0-c6cdfdbeaab2.png" width="250">

2. 취침 타이머를 적용할 앱을 선택한 후, 뒤로가기를 눌러 프로젝트 화면으로 복귀합니다.

<img src="https://user-images.githubusercontent.com/11005424/28619515-b403c4d0-7243-11e7-8b72-c8968ab489a0.png" width="250">

3. Tasker 우측 상단에 체크 버튼을 눌러 설정을 적용합니다.

<img src="https://user-images.githubusercontent.com/11005424/28619506-b3cd95e0-7243-11e7-84fd-e58f1a4fb217.png" width="250">

#### 접근성 권한

뒤로가기 버튼을 눌렀을 때, 다음과 같이 접근성 서비스가 꺼져 있다는 창이 뜨면 Yes를 눌러 Tasker를 허용해주어야 합니다.

<img src="https://user-images.githubusercontent.com/11005424/28619835-5a553a20-7245-11e7-8890-2b1197b6831e.png" width="250">

접근성 관련 설정 앱이 뜨면 다음과 같이 Tasker를 허용시켜 줍니다.

<img src="https://user-images.githubusercontent.com/11005424/28619896-9a20474e-7245-11e7-87d7-d9a2e099183b.png" width="500">

### 취침 타이머 적용

조건에 맞는 앱이 실행 중이면 노티바에 고정된 취침 타이머 알림이 생깁니다.

<img src="https://user-images.githubusercontent.com/11005424/28619509-b3e004dc-7243-11e7-858d-4ea5f0bbe498.png" width="250">

여기서 취침 타이머 설정 버튼을 클릭하면 시간을 설정할 수 있는 다이얼로그가 보여집니다. 원하는 시간을 선택한 후, 설정 버튼을 눌러 타이머를 시작합니다.

<img src="https://user-images.githubusercontent.com/11005424/28619989-03fe7e2e-7246-11e7-9435-0f7a3e5e158a.png" width="250">

### 재진입 허용

재진입 모드는 사용자가 취침 타이머를 적용한 앱에서 벗어났을 경우 5분의 유예 기간을 두어 잠시 딴짓을 할 수 있도록 해줍니다.

<img src="https://user-images.githubusercontent.com/11005424/28620220-fb79558e-7246-11e7-8fe5-3ee51e3e25ca.png" width="500">

즉, 유투브 영상을 보다 잠깐 카톡이 와서 답변하는 동안 취침 타이머가 꺼지는 것이 아니라 재진입 상태로 넘어가게 되고, 카톡 답장이 끝난 후 복귀하면 다시 타이머가 동작합니다.

하지만 재진입 허용을 켜게 되면 취침 타이머를 적용한 앱이 항상 Foreground에서 동작해야 합니다. 따라서 음악 앱과 같이 백그라운드에서 동작하는 경우에는 적용하기 힘들게 됩니다.

따라서 백그라운드에서 동작하는 앱의 경우에는 재진입 허용을 끄게 되면 처음 설정한 시간이 지나면 그 앱이 Foreground에 있는지 여부와 관계 없이 종료하게 됩니다.

## 알려진 문제

* getForegroundAppPkgName 테스크의 경우 실행 시간이 대략 10 ~ 15초 정도 소요됨
* 초단위 타이머 적용 시(0시간 0분 xx초), 테스크가 정상적으로 Wait 액션이 실행하지않고 종료되는 경우가 많음
* Scene에서 초기값을 적용해도 변수에 반영되지 않는 경우가 있음
* killApp 테스크에서 Intent가 정상적으로 반영되지 않는 경우가 있음
