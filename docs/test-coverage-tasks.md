# 🧪 테스트 커버리지 90% 달성 - 태스크 리스트

## 📅 Phase 1: 테스트 인프라 구축 (Week 1)

### 🔧 환경 설정
- [ ] **T1.1** pytest 및 관련 패키지 설치
  ```bash
  poetry add --group dev pytest pytest-cov pytest-mock pytest-asyncio factory-boy faker pytest-xdist
  ```
- [ ] **T1.2** 코드 품질 도구 설치
  ```bash
  poetry add --group dev black flake8 mypy
  ```

### 📁 테스트 디렉토리 구조 생성
- [ ] **T1.3** 기본 테스트 디렉토리 생성
  ```bash
  mkdir -p realworld/tests/{test_models,test_utils,test_validation,test_api,test_integration,factories}
  ```
- [ ] **T1.4** `__init__.py` 파일 생성
  ```bash
  touch realworld/tests/{test_models,test_utils,test_validation,test_api,test_integration,factories}/__init__.py
  ```

### ⚙️ 설정 파일 생성
- [ ] **T1.5** `pytest.ini` 생성
- [ ] **T1.6** `realworld/tests/conftest.py` 생성 (공통 픽스처)
- [ ] **T1.7** `realworld/tests/test_config.py` 생성 (테스트 설정)

### 🏭 테스트 데이터 팩토리 생성
- [ ] **T1.8** `realworld/tests/factories/user_factory.py` 생성
- [ ] **T1.9** `realworld/tests/factories/article_factory.py` 생성
- [ ] **T1.10** `realworld/tests/factories/comment_factory.py` 생성

### 🔄 CI/CD 설정
- [ ] **T1.11** `.github/workflows/test.yml` 생성
- [ ] **T1.12** 테스트 자동화 워크플로우 설정

---

## 📅 Phase 2: 단위 테스트 구현 (Week 2-4)

### 🏗️ Models 테스트 (Week 2)

#### Users Model
- [ ] **T2.1** `realworld/tests/test_models/test_users.py` 생성
- [ ] **T2.2** User 생성 테스트 구현
- [ ] **T2.3** 비밀번호 해싱 테스트 구현
- [ ] **T2.4** 사용자 조회 테스트 구현
- [ ] **T2.5** 사용자 삭제 테스트 구현
- [ ] **T2.6** 사용자 유효성 검증 테스트 구현

#### Articles Model
- [ ] **T2.7** `realworld/tests/test_models/test_articles.py` 생성
- [ ] **T2.8** Article CRUD 테스트 구현
- [ ] **T2.9** 슬러그 생성 테스트 구현
- [ ] **T2.10** 태그 관리 테스트 구현
- [ ] **T2.11** 좋아요 기능 테스트 구현

#### Comments Model
- [ ] **T2.12** `realworld/tests/test_models/test_comments.py` 생성
- [ ] **T2.13** Comment CRUD 테스트 구현
- [ ] **T2.14** 게시글-댓글 연관관계 테스트 구현

#### Profiles Model
- [ ] **T2.15** `realworld/tests/test_models/test_profiles.py` 생성
- [ ] **T2.16** Profile 모델 테스트 구현
- [ ] **T2.17** 팔로우/언팔로우 테스트 구현

### 🛠️ Utils 테스트 (Week 3)

#### JWT Utils
- [ ] **T2.18** `realworld/tests/test_utils/test_jwt.py` 확장
- [ ] **T2.19** 토큰 생성 테스트 강화
- [ ] **T2.20** 토큰 만료 테스트 구현
- [ ] **T2.21** 잘못된 토큰 처리 테스트 구현

#### Auth Utils
- [ ] **T2.22** `realworld/tests/test_utils/test_auth.py` 확장
- [ ] **T2.23** 인증 미들웨어 테스트 강화
- [ ] **T2.24** 권한 검증 테스트 구현

#### Slug Utils
- [ ] **T2.25** `realworld/tests/test_utils/test_slug.py` 확장
- [ ] **T2.26** 다양한 입력 슬러그 생성 테스트
- [ ] **T2.27** 중복 슬러그 처리 테스트 구현

#### Error Handling Utils
- [ ] **T2.28** `realworld/tests/test_utils/test_handle_errors.py` 생성
- [ ] **T2.29** 에러 핸들링 데코레이터 테스트 구현
- [ ] **T2.30** 다양한 예외 상황 테스트 구현

### ✅ Validation 테스트 (Week 4)

#### Auth Validation
- [ ] **T2.31** `realworld/tests/test_validation/test_auth.py` 생성
- [ ] **T2.32** 로그인 검증 테스트 구현
- [ ] **T2.33** 회원가입 검증 테스트 구현
- [ ] **T2.34** 잘못된 입력 데이터 처리 테스트

#### Articles Validation
- [ ] **T2.35** `realworld/tests/test_validation/test_articles.py` 생성
- [ ] **T2.36** 게시글 생성 검증 테스트 구현
- [ ] **T2.37** 게시글 수정 검증 테스트 구현
- [ ] **T2.38** 필수 필드 검증 테스트 구현

#### Comments Validation
- [ ] **T2.39** `realworld/tests/test_validation/test_comments.py` 생성
- [ ] **T2.40** 댓글 검증 테스트 구현

#### Profiles Validation
- [ ] **T2.41** `realworld/tests/test_validation/test_profiles.py` 생성
- [ ] **T2.42** 프로필 검증 테스트 구현

---

## 📅 Phase 3: 통합 테스트 구현 (Week 5-6)

### 🌐 API 엔드포인트 테스트 (Week 5)

#### Users API
- [ ] **T3.1** `realworld/tests/test_api/test_users_api.py` 생성
- [ ] **T3.2** POST /api/users (회원가입) 테스트
- [ ] **T3.3** POST /api/users/login (로그인) 테스트
- [ ] **T3.4** GET /api/user (현재 사용자 정보) 테스트
- [ ] **T3.5** PUT /api/user (사용자 정보 수정) 테스트

#### Articles API
- [ ] **T3.6** `realworld/tests/test_api/test_articles_api.py` 생성
- [ ] **T3.7** GET /api/articles (게시글 목록) 테스트
- [ ] **T3.8** GET /api/articles/:slug (게시글 상세) 테스트
- [ ] **T3.9** POST /api/articles (게시글 생성) 테스트
- [ ] **T3.10** PUT /api/articles/:slug (게시글 수정) 테스트
- [ ] **T3.11** DELETE /api/articles/:slug (게시글 삭제) 테스트
- [ ] **T3.12** POST /api/articles/:slug/favorite (좋아요) 테스트
- [ ] **T3.13** DELETE /api/articles/:slug/favorite (좋아요 취소) 테스트

#### Comments API
- [ ] **T3.14** `realworld/tests/test_api/test_comments_api.py` 생성
- [ ] **T3.15** GET /api/articles/:slug/comments (댓글 목록) 테스트
- [ ] **T3.16** POST /api/articles/:slug/comments (댓글 작성) 테스트
- [ ] **T3.17** DELETE /api/articles/:slug/comments/:id (댓글 삭제) 테스트

#### Profiles API
- [ ] **T3.18** `realworld/tests/test_api/test_profiles_api.py` 생성
- [ ] **T3.19** GET /api/profiles/:username (프로필 조회) 테스트
- [ ] **T3.20** POST /api/profiles/:username/follow (팔로우) 테스트
- [ ] **T3.21** DELETE /api/profiles/:username/follow (언팔로우) 테스트

### 🔐 통합 테스트 (Week 6)

#### Authentication Flow
- [ ] **T3.22** `realworld/tests/test_integration/test_auth_flow.py` 생성
- [ ] **T3.23** 전체 인증 플로우 테스트 구현
- [ ] **T3.24** 토큰 기반 API 접근 테스트 구현
- [ ] **T3.25** 권한 없는 접근 차단 테스트 구현

#### Database Integration
- [ ] **T3.26** `realworld/tests/test_integration/test_database.py` 생성
- [ ] **T3.27** 데이터베이스 연결 테스트 구현
- [ ] **T3.28** 트랜잭션 테스트 구현
- [ ] **T3.29** 데이터 일관성 테스트 구현

---

## 📅 Phase 4: 최적화 및 유지보수 (Week 7)

### ⚡ 성능 최적화
- [ ] **T4.1** 병렬 테스트 실행 설정
- [ ] **T4.2** 테스트 데이터 최적화
- [ ] **T4.3** 불필요한 테스트 제거
- [ ] **T4.4** 테스트 실행 시간 측정 및 최적화

### 📊 커버리지 분석
- [ ] **T4.5** 전체 커버리지 측정
- [ ] **T4.6** 90% 미달 모듈 식별 및 보완
- [ ] **T4.7** 커버리지 리포트 생성 자동화

### 📚 문서화
- [ ] **T4.8** 테스트 작성 가이드라인 문서 작성
- [ ] **T4.9** 새로운 기능 추가 시 테스트 작성 방법 문서화
- [ ] **T4.10** 커버리지 리포트 해석 방법 문서화
- [ ] **T4.11** README에 테스트 실행 방법 추가

### 🔄 CI/CD 최적화
- [ ] **T4.12** GitHub Actions 워크플로우 최적화
- [ ] **T4.13** 테스트 실패 시 알림 설정
- [ ] **T4.14** 커버리지 배지 추가

---

## 📈 진행 상황 체크리스트

### Week 1 완료 기준
- [ ] 모든 T1.x 태스크 완료
- [ ] 기본 테스트 실행 가능
- [ ] CI/CD 파이프라인 동작 확인

### Week 2 완료 기준
- [ ] 모든 T2.1-T2.17 태스크 완료
- [ ] Models 테스트 커버리지 95% 이상

### Week 3 완료 기준
- [ ] 모든 T2.18-T2.30 태스크 완료
- [ ] Utils 테스트 커버리지 90% 이상

### Week 4 완료 기준
- [ ] 모든 T2.31-T2.42 태스크 완료
- [ ] Validation 테스트 커버리지 90% 이상

### Week 5 완료 기준
- [ ] 모든 T3.1-T3.21 태스크 완료
- [ ] 모든 API 엔드포인트 테스트 완료

### Week 6 완료 기준
- [ ] 모든 T3.22-T3.29 태스크 완료
- [ ] 통합 테스트 커버리지 80% 이상

### Week 7 완료 기준
- [ ] 모든 T4.x 태스크 완료
- [ ] 전체 테스트 커버리지 90% 이상 달성
- [ ] 테스트 실행 시간 < 30초

---

## 🚀 빠른 시작 가이드

### 1. 환경 설정
```bash
# 의존성 설치
poetry add --group dev pytest pytest-cov pytest-mock pytest-asyncio factory-boy faker pytest-xdist black flake8 mypy

# 디렉토리 생성
mkdir -p realworld/tests/{test_models,test_utils,test_validation,test_api,test_integration,factories}

# __init__.py 파일 생성
find realworld/tests -type d -exec touch {}/__init__.py \;
```

### 2. 첫 번째 테스트 실행
```bash
# 현재 커버리지 확인
poetry run pytest --cov=realworld --cov-report=html

# 테스트 실행
poetry run pytest -v
```

### 3. 진행 상황 확인
```bash
# 커버리지 리포트 확인
open htmlcov/index.html

# 특정 모듈 커버리지 확인
poetry run pytest --cov=realworld.models --cov-report=term-missing
```

---

## 📞 도움이 필요할 때

### 블로커 발생 시
1. **테스트 환경 이슈**: conftest.py 설정 확인
2. **데이터베이스 연결 문제**: 테스트 DB 설정 확인
3. **Import 오류**: PYTHONPATH 설정 확인
4. **커버리지 측정 오류**: pytest.ini 설정 확인

### 리소스
- [pytest 공식 문서](https://docs.pytest.org/)
- [factory-boy 문서](https://factoryboy.readthedocs.io/)
- [pytest-cov 문서](https://pytest-cov.readthedocs.io/)

---

**총 태스크 수**: 86개  
**예상 완료 시간**: 7주  
**목표 커버리지**: 90% 이상
