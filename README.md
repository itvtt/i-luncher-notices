# i-luncher-notices

모든 i-luncher(일반 · 마스터)가 시작할 때와 새로고침할 때 이 저장소를 GitHub 에서 바로 읽습니다. 공개 저장소라 토큰이 필요 없습니다.

| 파일 | 내용 |
|---|---|
| [`공지.txt`](공지.txt) | 공지 |
| [`basic-apps.json`](basic-apps.json) + [`basic-media/`](basic-media) | 기본 목록: 모든 런처의 스토어에 보이는 앱과 스크린샷 |

고치는 법은 둘 다 같습니다: GitHub 에서 파일을 열어 연필(편집) → 고친 뒤 **Commit changes** 로 `main` 에 저장. 런처를 릴리스할 필요가 없습니다.

## 공지

i-luncher 의 관리자 메뉴 → 공지 → i-luncher → **GitHub에서 편집** 도 `공지.txt` 를 엽니다.

```
첫 공지 제목
본문 첫 줄
본문 둘째 줄
---
다음 공지 제목
본문
```

- 공지마다 **첫 줄은 제목**, 다음 줄부터 본문입니다.
- 공지 사이는 `---` 만 있는 줄입니다.
- 제목이 같으면 같은 공지입니다. 본문을 고치면 이미 읽은 사람에게도 다시 알립니다.
- 읽지 않은 공지는 런처 목록 위에 띠로 보입니다. 파일을 비우면 공지가 없습니다.

## 기본 목록

- **앱 더하기**: `basic-apps.json` 의 항목 하나를 복사해 고칩니다 (`id`, `name`, `repository` = 저장소 이름만, `category`, `description`, `details`, `author`, `installName`, `order`, `screenshots`).
- **스크린샷**: `basic-media/` 에 올리고 (**Add file → Upload files**) `screenshots` 에 파일 이름을 적습니다. 앱마다 3장 이상, 실제 앱 화면.
- 앱 저장소는 **공개**이고 릴리스(`<installName>-win-x64.zip`)가 있어야 일반 사용자가 받습니다.
- 목록에서 빼면 스토어에서 사라집니다 (이미 설치한 사람의 앱은 설치됨에 남음).
- 사용자가 스토어에서 지운 앱은 이 목록에 있어도 본인이 다시 추가할 때까지 그 사용자에게 나오지 않습니다.
- 형식이 틀리면 런처는 마지막으로 읽은 목록을 그대로 쓰고, 마스터 화면에 오류를 띄웁니다.
- 마스터는 이 목록에 API 서버의 서버 목록을 더해 봅니다 (같은 앱이면 서버 목록 값).

## 다른 곳에서 쓸 때

런처 빌드 설정 `NOTICES_REPOSITORY`(비우면 `i-luncher-notices`, 이름만 쓰면 런처 저장소와 같은 호스트 · 소유자), `NOTICES_PATH`(비우면 `공지.txt`), `BASIC_APPS_PATH`(비우면 `basic-apps.json`, 스크린샷은 그 옆 `basic-media/`)로 정합니다.
이 저장소에 `basic-apps.json` 이 없으면 런처는 자기 안에 든 목록(i-luncher 저장소의 `basic-apps.json` · `basic-media/`)을 씁니다. 새 환경에서는 그 두 개를 이 저장소에 복사해 시작합니다.
