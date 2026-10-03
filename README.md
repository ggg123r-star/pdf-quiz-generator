# 📚 PDF AI 문제 자동 생성기 — 링크 공유 버전

PDF를 업로드하면 AI가 PDF 내용을 바탕으로 4지선다 시험문제를 만들어 주는 Streamlit 웹앱입니다.

## 가장 쉬운 배포 방법: Streamlit Community Cloud

Streamlit Community Cloud는 GitHub 저장소의 앱을 배포하고 `streamlit.app` 주소를 만들어 줍니다.

### 1. GitHub 저장소 만들기

GitHub에서 새 저장소(repository)를 만들고 이 폴더의 파일을 모두 업로드합니다.

필수 파일:
- `app.py`
- `requirements.txt`

### 2. Streamlit Cloud 접속

https://share.streamlit.io/

GitHub로 로그인한 뒤 **Create app**을 선택합니다.

### 3. 저장소 선택

- Repository: 방금 만든 GitHub 저장소
- Branch: `main`
- Main file path: `app.py`

배포하면 `https://원하는주소.streamlit.app` 형태의 링크가 만들어집니다.

### 4. OpenAI API Key 설정

배포된 앱의 설정에서 **Secrets**에 아래처럼 입력할 수 있습니다.

```toml
OPENAI_API_KEY = "여기에_본인의_OpenAI_API_Key"
```

이렇게 하면 방문자가 API Key를 직접 입력하지 않아도 됩니다.

### ⚠️ 중요: 공개 링크에서 API 비용 보호

`OPENAI_API_KEY`를 설정한 앱을 누구나 사용할 수 있게 공개하면, 방문자가 문제를 생성할 때 그 API Key의 사용량과 비용이 발생할 수 있습니다.

그래서 여러 사람에게 링크를 공개할 예정이라면 사이트 비밀번호도 설정하는 것을 권장합니다.

```toml
OPENAI_API_KEY = "여기에_본인의_OpenAI_API_Key"
APP_PASSWORD = "친구들에게_공유할_사이트_비밀번호"
```

`APP_PASSWORD`를 설정하면 사이트 접속 시 비밀번호를 먼저 입력해야 합니다.

### 5. 주소 바꾸기

Streamlit Cloud의 App settings에서 원하는 사용 가능한 subdomain을 지정할 수 있습니다.

예:
`https://pdf-quiz-generator.streamlit.app`

## API Key를 사용자마다 입력하게 하고 싶다면

Secrets에 `OPENAI_API_KEY`를 넣지 않으면 앱 왼쪽 메뉴에서 각 사용자가 자신의 API Key를 입력할 수 있습니다.

이 방식에서는 앱 운영자의 API Key를 공유하지 않습니다.

## 현재 기능

- PDF 업로드
- PDF 텍스트 추출
- 1~50문제 생성
- 4지선다
- 난이도 하/중/상
- 혼합형/개념형/옳은 것·옳지 않은 것/임상 상황형/사례형
- 정답 및 해설
- 시험지 TXT 다운로드
- 정답·해설 TXT 다운로드
- Streamlit Cloud 링크 공유

## 참고

현재 버전은 텍스트 기반 PDF를 대상으로 합니다. 스캔 이미지 PDF는 OCR 기능을 추가해야 합니다.
