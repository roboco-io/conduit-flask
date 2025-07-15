# ![RealWorld Example App](logo.png) Conduit Flask - RealWorld 블로그 플랫폼

> ### Python + Flask + Couchbase로 구현된 실제 운영 수준의 블로그 플랫폼입니다. CRUD 작업, 인증, 고급 패턴 등을 포함하며 [RealWorld](https://github.com/gothinkster/realworld) 스펙과 API를 준수합니다.

### [데모](https://demo.realworld.io/)&nbsp;&nbsp;&nbsp;&nbsp;[RealWorld](https://github.com/gothinkster/realworld)

이 코드베이스는 Python + Flask + Couchbase를 사용하여 CRUD 작업, 인증, 라우팅, 페이지네이션 등을 포함한 완전한 풀스택 애플리케이션을 구현한 예제입니다.

Flask 커뮤니티의 스타일 가이드와 모범 사례를 철저히 준수하여 개발되었습니다.

다른 프론트엔드/백엔드와의 연동 방법에 대한 자세한 정보는 [RealWorld](https://github.com/gothinkster/realworld) 저장소를 참조하세요.

## 🏗️ 프로젝트 구조

```text
conduit-flask/
├── realworld/
│   ├── app.py              # Flask 애플리케이션 진입점
│   ├── db.py               # Couchbase 데이터베이스 연결
│   ├── extensions.py       # Flask 확장 모듈
│   ├── models/             # 데이터 모델
│   │   ├── users.py        # 사용자 모델
│   │   ├── articles.py     # 게시글 모델
│   │   ├── comments.py     # 댓글 모델
│   │   └── profiles.py     # 프로필 모델
│   ├── routes/v1/          # API 라우트 (v1)
│   │   ├── users.py        # 사용자 관련 API
│   │   ├── articles.py     # 게시글 관련 API
│   │   ├── comments.py     # 댓글 관련 API
│   │   └── profiles.py     # 프로필 관련 API
│   ├── utils/              # 유틸리티 함수들
│   ├── validation/         # 데이터 검증 모듈
│   ├── tests/              # 테스트 파일
│   └── postman/            # Postman 컬렉션
├── pyproject.toml          # Poetry 의존성 관리
├── poetry.lock             # 의존성 잠금 파일
└── README.md               # 프로젝트 문서
```

## 🚀 기술 스택

- **백엔드**: Python 3.11+, Flask 3.0+
- **데이터베이스**: Couchbase NoSQL
- **인증**: JWT (JSON Web Token)
- **API 문서**: Flask-RESTX
- **의존성 관리**: Poetry
- **보안**: bcrypt 해싱

## 📋 주요 기능

- ✅ 사용자 회원가입/로그인
- ✅ JWT 기반 인증 시스템
- ✅ 게시글 CRUD (생성, 읽기, 수정, 삭제)
- ✅ 댓글 시스템
- ✅ 사용자 프로필 관리
- ✅ 게시글 좋아요/북마크
- ✅ 사용자 팔로우/언팔로우
- ✅ 태그 기반 게시글 분류
- ✅ 페이지네이션
- ✅ RESTful API 설계

## 🛠️ 설치 및 실행

### 1. 환경 설정

1. 프로젝트를 클론합니다:
   ```bash
   git clone <repository-url>
   cd conduit-flask
   ```

2. `realworld` 디렉토리로 이동하여 `.env` 파일을 생성합니다:
   ```bash
   cd realworld
   cp .env.example .env
   ```

3. `.env` 파일에 Couchbase 데이터베이스 정보를 입력합니다:

   ```env
   DB_CONNECTION_STRING=couchbase://localhost
   DB_USERNAME=your_username
   DB_PASSWORD=your_password
   SECRET_KEY=your_secret_key_for_jwt
   ```

### 2. 의존성 설치

```bash
# Poetry가 설치되어 있지 않다면
curl -sSL https://install.python-poetry.org | python3 -

# 의존성 설치
poetry install
```

### 3. 애플리케이션 실행

```bash
# 개발 서버 실행
poetry run python realworld/app.py

# 또는 Poetry 스크립트 사용
poetry run server
```

서버가 성공적으로 시작되면 `http://localhost:8080`에서 API에 접근할 수 있습니다.

## 🧪 테스트

```bash
# 테스트 실행
poetry run pytest realworld/tests/
```

## 📚 API 문서

애플리케이션이 실행된 후 다음 엔드포인트에서 API 문서를 확인할 수 있습니다:

- Swagger UI: `http://localhost:8080/doc`

### 주요 API 엔드포인트

- `POST /api/v1/users/login` - 사용자 로그인
- `POST /api/v1/users` - 사용자 회원가입
- `GET /api/v1/articles` - 게시글 목록 조회
- `POST /api/v1/articles` - 게시글 작성
- `GET /api/v1/articles/{slug}` - 특정 게시글 조회
- `POST /api/v1/articles/{slug}/comments` - 댓글 작성
- `GET /api/v1/profiles/{username}` - 사용자 프로필 조회

## 🔧 개발 환경 설정

### Couchbase 설정

1. Couchbase Server를 설치하고 실행합니다
2. 새 버킷을 생성합니다 (예: `realworld`)
3. 사용자 계정을 생성하고 적절한 권한을 부여합니다
4. `.env` 파일에 연결 정보를 입력합니다

### 코드 스타일

이 프로젝트는 다음 코딩 표준을 따릅니다:

- PEP 8 Python 스타일 가이드
- Flask 모범 사례
- Clean Architecture 원칙

## 🤝 기여하기

1. 이 저장소를 포크합니다
2. 새 기능 브랜치를 생성합니다 (`git checkout -b feature/amazing-feature`)
3. 변경사항을 커밋합니다 (`git commit -m 'Add some amazing feature'`)
4. 브랜치에 푸시합니다 (`git push origin feature/amazing-feature`)
5. Pull Request를 생성합니다

## 📄 라이선스

이 프로젝트는 MIT 라이선스 하에 배포됩니다. 자세한 내용은 `LICENSE` 파일을 참조하세요.

## 🔗 관련 링크

- [RealWorld 프로젝트](https://github.com/gothinkster/realworld)
- [Flask 공식 문서](https://flask.palletsprojects.com/)
- [Couchbase Python SDK](https://docs.couchbase.com/python-sdk/current/hello-world/start-using-sdk.html)
- [Poetry 문서](https://python-poetry.org/docs/)
