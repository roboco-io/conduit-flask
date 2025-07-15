# 🧪 테스트 커버리지 90% 달성 프로젝트 계획서

## 📋 프로젝트 개요

### 목표
- **현재 테스트 커버리지**: ~5% (1개 테스트 파일만 존재)
- **목표 테스트 커버리지**: 90% 이상
- **총 코드 라인 수**: 약 1,246 라인
- **예상 테스트 코드**: 약 2,000+ 라인 추가 필요

### 성공 기준
- [ ] 단위 테스트 커버리지 90% 이상
- [ ] 통합 테스트 커버리지 80% 이상
- [ ] 모든 API 엔드포인트 테스트 완료
- [ ] CI/CD 파이프라인에서 자동 테스트 실행
- [ ] 테스트 실행 시간 < 30초

## 🎯 해결 전략 개요

### Phase 1: 테스트 인프라 구축 (1주)
- pytest 기반 테스트 환경 설정
- 테스트 데이터베이스 설정
- 커버리지 측정 도구 설정
- CI/CD 파이프라인 구축

### Phase 2: 단위 테스트 구현 (2-3주)
- 모델 레이어 테스트
- 유틸리티 함수 테스트
- 검증 로직 테스트

### Phase 3: 통합 테스트 구현 (2주)
- API 엔드포인트 테스트
- 인증/인가 테스트
- 데이터베이스 연동 테스트

### Phase 4: 최적화 및 유지보수 (1주)
- 테스트 성능 최적화
- 문서화 완성
- 팀 교육 자료 작성

## 📊 현재 상태 분석

### 기존 테스트 현황
```
realworld/tests/
├── __init__.py
└── test_utils.py (JWT, 인증, 슬러그 생성 테스트)
```

### 테스트가 필요한 모듈 분석

| 모듈 | 파일 수 | 예상 복잡도 | 우선순위 |
|------|---------|-------------|----------|
| **Models** | 4개 | High | 🔴 Critical |
| **Routes/API** | 4개 | High | 🔴 Critical |
| **Utils** | 4개 | Medium | 🟠 High |
| **Validation** | 5개 | Medium | 🟠 High |
| **Core** | 3개 | Low | 🟡 Medium |

## 🏗️ 상세 구현 계획

### Phase 1: 테스트 인프라 구축 (Week 1)

#### 1.1 테스트 환경 설정
```bash
# 새로운 의존성 추가
poetry add --group dev pytest pytest-cov pytest-mock pytest-asyncio factory-boy faker
```

#### 1.2 테스트 설정 파일 생성
- `pytest.ini`: pytest 설정
- `conftest.py`: 공통 픽스처 정의
- `test_config.py`: 테스트 전용 설정

#### 1.3 테스트 데이터베이스 설정
- 테스트 전용 Couchbase 버킷 설정
- 테스트 데이터 초기화/정리 로직

#### 1.4 CI/CD 파이프라인
- GitHub Actions 워크플로우 설정
- 자동 테스트 실행 및 커버리지 리포트

### Phase 2: 단위 테스트 구현 (Week 2-4)

#### 2.1 Models 테스트 (우선순위: 🔴 Critical)

**`test_models/test_users.py`**
- [ ] User 모델 생성/저장 테스트
- [ ] 비밀번호 해싱 테스트
- [ ] 사용자 조회 테스트
- [ ] 사용자 삭제 테스트
- [ ] 유효성 검증 테스트

**`test_models/test_articles.py`**
- [ ] Article 모델 CRUD 테스트
- [ ] 슬러그 생성 테스트
- [ ] 태그 관리 테스트
- [ ] 좋아요 기능 테스트

**`test_models/test_comments.py`**
- [ ] Comment 모델 CRUD 테스트
- [ ] 게시글-댓글 연관관계 테스트

**`test_models/test_profiles.py`**
- [ ] Profile 모델 테스트
- [ ] 팔로우/언팔로우 테스트

#### 2.2 Utils 테스트 (우선순위: 🟠 High)

**`test_utils/test_jwt.py`** (기존 확장)
- [ ] 토큰 생성 테스트 강화
- [ ] 토큰 만료 테스트
- [ ] 잘못된 토큰 처리 테스트

**`test_utils/test_auth.py`** (기존 확장)
- [ ] 인증 미들웨어 테스트 강화
- [ ] 권한 검증 테스트

**`test_utils/test_slug.py`** (기존 확장)
- [ ] 다양한 입력에 대한 슬러그 생성 테스트
- [ ] 중복 슬러그 처리 테스트

**`test_utils/test_handle_errors.py`**
- [ ] 에러 핸들링 데코레이터 테스트
- [ ] 다양한 예외 상황 테스트

#### 2.3 Validation 테스트 (우선순위: 🟠 High)

**`test_validation/test_auth.py`**
- [ ] 로그인/회원가입 검증 테스트
- [ ] 잘못된 입력 데이터 처리 테스트

**`test_validation/test_articles.py`**
- [ ] 게시글 생성/수정 검증 테스트
- [ ] 필수 필드 검증 테스트

**`test_validation/test_comments.py`**
- [ ] 댓글 검증 테스트

**`test_validation/test_profiles.py`**
- [ ] 프로필 검증 테스트

### Phase 3: 통합 테스트 구현 (Week 5-6)

#### 3.1 API 엔드포인트 테스트

**`test_api/test_users_api.py`**
- [ ] POST /api/users (회원가입)
- [ ] POST /api/users/login (로그인)
- [ ] GET /api/user (현재 사용자 정보)
- [ ] PUT /api/user (사용자 정보 수정)

**`test_api/test_articles_api.py`**
- [ ] GET /api/articles (게시글 목록)
- [ ] GET /api/articles/:slug (게시글 상세)
- [ ] POST /api/articles (게시글 생성)
- [ ] PUT /api/articles/:slug (게시글 수정)
- [ ] DELETE /api/articles/:slug (게시글 삭제)
- [ ] POST /api/articles/:slug/favorite (좋아요)
- [ ] DELETE /api/articles/:slug/favorite (좋아요 취소)

**`test_api/test_comments_api.py`**
- [ ] GET /api/articles/:slug/comments (댓글 목록)
- [ ] POST /api/articles/:slug/comments (댓글 작성)
- [ ] DELETE /api/articles/:slug/comments/:id (댓글 삭제)

**`test_api/test_profiles_api.py`**
- [ ] GET /api/profiles/:username (프로필 조회)
- [ ] POST /api/profiles/:username/follow (팔로우)
- [ ] DELETE /api/profiles/:username/follow (언팔로우)

#### 3.2 인증/인가 테스트

**`test_integration/test_auth_flow.py`**
- [ ] 전체 인증 플로우 테스트
- [ ] 토큰 기반 API 접근 테스트
- [ ] 권한 없는 접근 차단 테스트

#### 3.3 데이터베이스 연동 테스트

**`test_integration/test_database.py`**
- [ ] 데이터베이스 연결 테스트
- [ ] 트랜잭션 테스트
- [ ] 데이터 일관성 테스트

### Phase 4: 최적화 및 유지보수 (Week 7)

#### 4.1 테스트 성능 최적화
- [ ] 병렬 테스트 실행 설정
- [ ] 테스트 데이터 최적화
- [ ] 불필요한 테스트 제거

#### 4.2 문서화
- [ ] 테스트 작성 가이드라인
- [ ] 새로운 기능 추가 시 테스트 작성 방법
- [ ] 커버리지 리포트 해석 방법

## 🛠️ 필요한 도구 및 라이브러리

### 테스트 프레임워크
```toml
[tool.poetry.group.dev.dependencies]
pytest = "^7.4.0"
pytest-cov = "^4.1.0"
pytest-mock = "^3.11.1"
pytest-asyncio = "^0.21.1"
pytest-xdist = "^3.3.1"  # 병렬 실행
```

### 테스트 데이터 생성
```toml
factory-boy = "^3.3.0"
faker = "^19.6.2"
```

### 코드 품질
```toml
black = "^23.7.0"
flake8 = "^6.0.0"
mypy = "^1.5.1"
```

## 📁 예상 테스트 디렉토리 구조

```
realworld/tests/
├── __init__.py
├── conftest.py                 # 공통 픽스처
├── test_config.py             # 테스트 설정
├── factories/                 # 테스트 데이터 팩토리
│   ├── __init__.py
│   ├── user_factory.py
│   ├── article_factory.py
│   └── comment_factory.py
├── test_models/               # 모델 단위 테스트
│   ├── __init__.py
│   ├── test_users.py
│   ├── test_articles.py
│   ├── test_comments.py
│   └── test_profiles.py
├── test_utils/                # 유틸리티 테스트
│   ├── __init__.py
│   ├── test_jwt.py
│   ├── test_auth.py
│   ├── test_slug.py
│   └── test_handle_errors.py
├── test_validation/           # 검증 로직 테스트
│   ├── __init__.py
│   ├── test_auth.py
│   ├── test_articles.py
│   ├── test_comments.py
│   └── test_profiles.py
├── test_api/                  # API 엔드포인트 테스트
│   ├── __init__.py
│   ├── test_users_api.py
│   ├── test_articles_api.py
│   ├── test_comments_api.py
│   └── test_profiles_api.py
└── test_integration/          # 통합 테스트
    ├── __init__.py
    ├── test_auth_flow.py
    └── test_database.py
```

## 📈 진행 상황 추적

### 주간 마일스톤

**Week 1: 인프라 구축**
- [ ] 테스트 환경 설정 완료
- [ ] CI/CD 파이프라인 구축
- [ ] 기본 픽스처 및 팩토리 생성

**Week 2-3: 핵심 모듈 테스트**
- [ ] Models 테스트 완료 (목표: 95% 커버리지)
- [ ] Utils 테스트 완료 (목표: 90% 커버리지)

**Week 4: 검증 로직 테스트**
- [ ] Validation 테스트 완료 (목표: 90% 커버리지)

**Week 5-6: API 통합 테스트**
- [ ] 모든 API 엔드포인트 테스트 완료
- [ ] 인증/인가 플로우 테스트 완료

**Week 7: 최적화 및 문서화**
- [ ] 전체 커버리지 90% 달성
- [ ] 테스트 실행 시간 최적화
- [ ] 문서화 완료

### 커버리지 목표

| 모듈 | 현재 | 목표 | 우선순위 |
|------|------|------|----------|
| Models | 0% | 95% | 🔴 Critical |
| Routes | 0% | 90% | 🔴 Critical |
| Utils | 30% | 90% | 🟠 High |
| Validation | 0% | 90% | 🟠 High |
| Core | 0% | 80% | 🟡 Medium |
| **전체** | **~5%** | **90%** | **목표** |

## 🚀 실행 계획

### 즉시 시작 가능한 작업

1. **테스트 환경 설정**
   ```bash
   poetry add --group dev pytest pytest-cov pytest-mock factory-boy faker
   ```

2. **기본 테스트 구조 생성**
   ```bash
   mkdir -p realworld/tests/{test_models,test_utils,test_validation,test_api,test_integration,factories}
   ```

3. **pytest 설정 파일 생성**
   - `pytest.ini`
   - `conftest.py`

### 팀 협업 방안

- **코드 리뷰**: 모든 테스트 코드는 리뷰 필수
- **페어 프로그래밍**: 복잡한 통합 테스트는 페어로 작성
- **일일 스탠드업**: 진행 상황 및 블로커 공유

## 📊 성공 측정 지표

### 정량적 지표
- [ ] 테스트 커버리지 90% 이상
- [ ] 테스트 실행 시간 < 30초
- [ ] 테스트 성공률 100%
- [ ] CI/CD 파이프라인 통과율 95% 이상

### 정성적 지표
- [ ] 새로운 기능 추가 시 테스트 작성 습관화
- [ ] 버그 발견 및 수정 시간 단축
- [ ] 코드 변경에 대한 신뢰도 향상
- [ ] 리팩토링 안전성 확보

## 🎯 예상 결과물

1. **90% 이상의 테스트 커버리지**
2. **약 50+ 개의 테스트 케이스**
3. **자동화된 CI/CD 파이프라인**
4. **테스트 작성 가이드라인 문서**
5. **지속 가능한 테스트 문화 구축**

---

**프로젝트 기간**: 7주  
**예상 투입 시간**: 80-100시간  
**담당자**: 개발팀  
**검토자**: 시니어 개발자  

이 계획을 통해 안정적이고 신뢰할 수 있는 코드베이스를 구축하여, 향후 기능 추가와 유지보수를 더욱 효율적으로 수행할 수 있을 것입니다.
