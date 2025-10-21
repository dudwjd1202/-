사용자님의 요청에 따라, `README.md` 파일에서 **'🚀 시작하는 방법'** 섹션부터 **'📄 라이선스'** 섹션까지를 삭제하고 새로운 내용으로 대체하여 다시 작성해 드리겠습니다.

-----

# 🤖 Assignment Auto-Scheduler: AI 기반 강의 과제 자동 캘린더 등록 앱

[]()
[]()
[]()
[]()

## 📌 프로젝트 소개

`Assignment Auto-Scheduler`는 **강의 중 교수님의 과제 지시 사항을 음성으로 인식**하고, \*\*인공지능(AI) 기반의 자연어 처리(NLP)\*\*를 통해 **핵심 마감 정보를 추출**하여 **사용자의 캘린더에 자동으로 일정을 등록**해주는 안드로이드 애플리케이션입니다.

더 이상 수업 중 급하게 메모하거나 과제 마감일을 잊어버릴 염려가 없습니다\!

## ✨ 주요 기능

| 기능 카테고리 | 상세 기능 | AI/기술 활용 |
| :--- | :--- | :--- |
| **🎙️ 실시간 음성 인식** | 강의 중 교수님의 음성을 실시간으로 텍스트로 변환 | **STT (Speech-to-Text) API** (Google Speech Recognizer/ML Kit) |
| **🧠 핵심 정보 추출** | 변환된 텍스트에서 과제 **제목** 및 **마감 날짜/시간** 자동 추출 | **NLP** (정규 표현식 또는 Custom NER) |
| **🗓️ 캘린더 자동 등록** | 추출된 정보로 안드로이드 캘린더에 새 이벤트 자동 생성 | **Android Calendar Provider** 또는 Generic Calendar API |
| **📝 사용자 확인 및 수정** | 등록 전 추출된 정보(제목, 마감일)를 확인하고 수정할 수 있는 UI 제공 | 사용자 친화적인 UI/UX 설계 |

## 🛠️ 기술 스택 (Tech Stack)

  * **프론트엔드/로직:** Kotlin (Android Native)
  * **AI/ML:**
      * **STT:** Google Cloud Speech-to-Text 또는 Firebase ML Kit
      * **NLP/NER:** 정규 표현식 및 키워드 매칭 (초기), TensorFlow Lite 기반의 커스텀 NER 모델 (고도화)
  * **데이터 관리:** Android Calendar Provider API
  * **개발 환경:** Android Studio

-----

## 🚀 개발 환경 설정 및 빌드 (Setup & Build)

### 1\. 사전 준비 사항

  * **Android Studio** 최신 버전
  * **Java Development Kit (JDK)**
  * **Android SDK** (Min. API 21 이상 권장)
  * **Firebase 계정** (선택 사항, ML Kit 사용 시 필요)

### 2\. 프로젝트 클론 및 열기

```bash
# GitHub에서 프로젝트 레포지토리 클론
git clone [YOUR_REPOSITORY_URL_HERE]
cd Assignment-Auto-Scheduler
```

  * **Android Studio**를 실행하고, `File` \> `Open`을 선택하여 클론한 프로젝트 폴더를 엽니다.

### 3\. API 키 및 권한 설정

  * **Firebase/Google Cloud 설정 (STT):** 클라우드 기반 STT를 사용하는 경우, 해당 API 키 또는 `google-services.json` 파일을 프로젝트에 추가해야 합니다.
  * **AndroidManifest.xml:** 다음 필수 권한이 `AndroidManifest.xml`에 추가되었는지 확인합니다.
    ```xml
    <uses-permission android:name="android.permission.RECORD_AUDIO" />
    <uses-permission android:name="android.permission.WRITE_CALENDAR" />
    <uses-permission android:name="android.permission.INTERNET" />
    ```

### 4\. 앱 빌드 및 실행

1.  Android Studio의 툴바에서 **Clean Project** 및 **Rebuild Project**를 실행합니다.
2.  에뮬레이터 또는 실제 안드로이드 기기를 연결합니다.
3.  **Run 'app'** 버튼을 클릭하여 앱을 빌드하고 실행합니다.

-----

## ⚙️ 구현 세부 사항

### 1\. 과제 정보 추출 로직 (NLP)

초기 버전에서는 효율성을 위해 다음과 같은 키워드 기반의 패턴 매칭을 활용할 수 있습니다.

  * **키워드 필터링:** "과제", "숙제", "제출", "마감" 등의 키워드가 포함된 문장만 분석합니다.
  * **날짜/시간 정규 표현식:** "이번 주 금요일", "다음 주 화요일 오후 5시", "2024년 12월 31일"과 같은 패턴을 인식하여 시스템 날짜 형식으로 변환하는 로직을 구현합니다.
  * **제목 유추:** 키워드와 날짜 정보를 제외한 나머지 텍스트를 잠정적인 과제 제목으로 설정합니다.

### 2\. 캘린더 연동 상세

추출된 마감 날짜를 기반으로 캘린더 이벤트 생성 시, 알림(Reminder) 기능을 기본으로 설정하여 사용자가 마감일을 놓치지 않도록 할 수 있습니다.

  * **알림 설정:** 마감일 1일 전, 또는 3시간 전에 알림이 울리도록 기본 설정 (사용자 설정 가능).
