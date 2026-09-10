# 특이점이왔다 — 그록 실행가이드 (Aside · Flow · 자막 · SNS)

> **역할:** 그록/실행 에이전트가 **후반 실행**할 때 본다 (Aside, Flow, 자막 분할, SNS 업로드).  
> **헌법(대본·연출·G게이트·유튜브 메타 뼈대):** `특이점이왔다_마스터_통합제작가이드.md` — **여기 있는 규칙을 다시 쓰지 말고 가리킨다.**  
> **TTS 보이스:** 마스터 확정 — Cartesia **`필재거제`** (구 Taehyun 경로 폐기).  
> **작성/갱신:** 2026-09-08 · 원우 — 마스터에 없는 실행락만 이 문서로.

---

## 0. 마스터와 역할 분담

| 문서 | 담당 |
| :--- | :--- |
| 마스터 PART A | Gemini 대본·옴니 프롬프트·시그니처·R/B/G·G1 |
| 마스터 PART B | TTS(필재거제 1.3)·묵음·Palmier 조립 뼈대·bed -8·VITRO31·YT 업로드 |
| **이 가이드** | Aside CLI · Flow 계정 우회 · **자막 스플리터** · **로고 파일경로** · **컷 stretch** · **SNS 전채널 실행** |
| `_LIVE-3장/이번편.md` | 그 편 팩트·경로·실측 초 |

---

## 1. Aside CLI

- 도구: 맥 **Aside CLI** (`aside`)
- 자동화: **`aside repl --account u0`** (JS). Flow/SNS/캡션 수정에 `aside exec` / bare LLM aside **금지**
- 세션: 매 잡 **새 repl**. 죽은 `--session` 재사용 금지
- 탭: leftover SE/Drive에 `goto` 덮지 말 것 · Flow/X **전용 탭** · 나가기 알람은 dismiss(취소)
- Flow와 SNS Aside를 **동시 단일 u0으로 싸우지 말 것** → 한 번에 한 스트림
- 형제: `Threads공장/Aside-제어락-2026-09-05.md` (알람·탭 분산)

---

## 2. Google Flow (스틸 · Omni I2V)

| 항목 | 잠금 |
| :--- | :--- |
| 비율 | **9:16** native (가로→세로 크롭 금지) |
| Omni | 10s 멀티샷 I2V · 클립당 **고유 스틸 1장** (형제컷 수렴 금지) |
| 성공분 | KEEP · 맹재생성 금지 |
| 킥 실패 | 같은 프롬프트 무한 재킥 금지 · 리더 보고 |
| 클립수 | `ceil(실측 VO초 / 10)` (마스터 클립 범위와 맞출 것) · 기획추정 자/초는 **마스터 1-B** |
| Spatial | Omni·팔미어·번인 태그 **Spatial typography 금지** (화면글자·HUD·떠다니는 라벨 프롬프트 금지) |
| 시각일치 | **마스터 3-C** — 랜드마크 고유토큰·머니샷 기하·기전=스틸선행 I2V · T2V 직행 금지 |
| KEEP 전 QC | ①랜드마크식별 ②현대감 ③기전형상 ④가짜텍스트없음 ⑤카메라홀드없음 — **하나라도 NO면 폐기** |

### 계정 우회 (원우 락)

1. `j2w0210@gmail.com`  
2. `j2w7777777@gmail.com`  

**사용량 있는 쪽으로 Flow.** 막히면 다른 계정. 성공분 KEEP. STATUS에 `account=` / `/u/N/` / project id. 둘 다 막히면 STOP.

---



## 3. TTS 속도 (편집)

- 생성: 마스터대로 Cartesia **필재거제** (`28e435b6-ce02-4798-b160-69157f321fc4`) · model **`sonic-3.6`** · speed **1.3**. `yoon`/`9a300938…` 금지.
- **Palmier/캡컷에서 VO 재생속도 추가 인상(1.1 등) 하지 말 것.** 필재거제 1.3 생성이 구 Taehyun+편집1.1과 체감 속도가 비슷함 (2026-09-08 원우).
- ffmpeg `atempo`로 한 번 더 올리는 것도 금지.
- 기획 음절→초 환산·예상 클립: **마스터 1-B** (≈7.7자/초). 추정으로 Omni 금지.

## 4. 자막 스플리터 (실행)

마스터: 번인 1어절 · VITRO31 · y≈0.5844 · 종결어미 다음 문장 합치기 금지.  
**아래는 마스터에 없던 실행 경로·세부.**

| 항목       | 값                                                                        |
| :------- | :----------------------------------------------------------------------- |
| 도구       | `Leedogin/korean-subtitle-splitter`                                      |
| 경로       | `/Users/j2w/AI_work/tools/korean-subtitle-splitter`                      |
| 적용       | `/Users/j2w/AI_work/tools/kss_apply_srt.py`                              |
| 어절       | 쇼츠 1–2어절. README 8어절 기본값 **쓰지 말 것**                                      |
| 6자 규칙    | 현재+다음(문장부호 제외) 합 ≤6이면 한 큐로 붙임 (자연스러울 때만)                                 |
| 금지       | `습니다/거든요/죠` 끝과 **다음 문장** 합치기                                             |
| COMPOUND | 조사·보조용언·의존명사·수량+단위·복합명사 · **그 편 물건명 → COMPOUND_TERMS**                   |
| 날짜 캡션    | 한 큐 `2011년3월11일` (연/월/일 쪼개지 않음)                                          |
| 폰트 파일    | `/Users/j2w/Library/Fonts/비트로코어TTF.ttf` (Premiere Heavy 63 ↔ Palmier 31) |
| 윤곽       | 자막 outline **1**                                                         |
| 플래시      | 0.3초급 자막/컷 금지                                                            |

스킬: `korean-subtitle-split` (에이전트 워크플로).

---

## 5. 로고 · 컷 stretch (실행)

### 로고

| 항목 | 값 |
| :--- | :--- |
| SVG | `/Users/j2w/AI_work/singularity/brand/logos/특이점이왔다_logo_lock.svg` |
| PNG | `/Users/j2w/AI_work/singularity/brand/logos/특이점이왔다_logo_lock.png` |
| 배치 | 가로 **756** · **y=118** · 가운데 · **첨~끝** |
| 비율 | **유튜브 원본 비율** 유지. 세로로 늘린 tall bake **금지** (2026-09-08 원우) |
| 상단 문자 | **채널 로고만**. 에피소드 제목·상단 강조 포스터·타이틀 카드 **넣지 않음** (2026-09-08 원우) |
| 금지 | `burn_logo.sh` 일괄 실행(타 편까지 재번인) · brand 마스터 PNG 함부로 덮어쓰기 |

### 컷

- 샷 최소 **2.0초** (마스터와 동일)
- 소스 부족 시 stretch **≤1.15** (`MAX_STRETCH=1.15`). 루프/freeze/tpad 금지
- Omni 현장음 **뮤트 금지** · bed는 마스터 **-7~-9 (기본 -8)**
- (선택) `omni_speech.py` → `edit/omni_speech.json` TALKER 검사

---

## 6. SNS 업로드 (유튜브 외) — 실행 SSoT

마스터 B-③ = 유튜브만. **여기가 전채널 SNS 실행본.**  
제휴(쿠팡) Threads공장 문체와 **섞지 말 것.**

### 공통

| 항목 | 잠금 |
| :--- | :--- |
| API | `/Users/j2w/AI_work/shopping/sns_post.py` + 옆 `.env` |
| 박스 브라우저 | SNS 업로드에 금지 (로봇). 필요 시 맥 Aside / 원우 웨일 |
| 예약 | 전채널 **유튜브 `publishAt`과 같은 KST 시각** (새벽 즉시 남발 금지) |
| 상단 제목 | **안 넣음**. 채널 로고만. 에피소드 제목/강조 포스터는 YT·SNS 영상 전부 미번인 |
| 끝난 뒤 | 다음 편 혼자 시작 금지 |

### YouTube (참조)

- 스크립트·토큰·채널ID = **마스터 B-③**
- 예약본은 파일만 갈아끼우기 불가 → **새 업로드 후 구 videoId 삭제** · SNS 링크 갱신

### Instagram

- 캡션 = **유튜브 설명란 그대로** + 푸터 3줄:  
  1) `영상 제작 필요한 사람, 댓글 달면 제작 md 파일 줌`  
  2) `구독 부탁합니다 
  3) `https://youtu.be/{id}`  
- 봇 한 줄+해시태그 도배 금지  
- published 캡션 수정 = Aside `repl` u0 (앱 수동 금지)  
- rupload 실패 시 litterbox/catbox **video_url** 폴백(실측 허용) · 쇼핑 광고글 손대지 말 것

### Threads (@j2w7777777)

- 페르소나 SSoT: `특이점이왔다 쓰레드페르소나.md` (해여/할게여/해주십셔 · 구독 구걸 금지)
- **5슬롯 로테이션** · 추적: `singularity/sns/threads_slot.txt` (및 편별 sns 폴더)
- 게이트: `쓰레드업로드게이트.md`
- 업로드 직전 **Humanize KR** (`im-not-ai` / 스킬 `threads-humanize-rotate`)
- 매편 같은 템플릿 금지 · 유튜브 설명란 복붙 금지

### X

- 짧게 + `https://youtu.be/{id}`  
- 미디어 정책은 그 편 브리프 따름 (링크만/영상)

### TikTok

- 제목·해시태그 = 유튜브와 **동일**
- Content API 공개 미검증 → **인박스 초안(SEND_TO_USER_INBOX)만**
- 64MB 초과 시 ~10MB 청크 · 공개는 원우가 인박스에서

---

## 7. 하지 말 것

- 영상 **상단에 에피소드 제목**/타이틀 카드/강조 포스터 넣기 (채널 로고만)

- 마스터 규칙을 이 문서에 장문 복붙
- Taehyun을 새 편 기본 TTS로 되살리기 (필재거제 = 마스터)
- 로고 tall bake / 비균등 늘림 후 Scale%로 깨기
- 구 `제작가이드.md`만 믿고 마스터·이 가이드를 건너뛰기
- 제휴 공장 멘트를 특이점 Threads에 재사용

---

## 한 줄 요약

**헌법=마스터(필재거제). 실행=Aside·Flow 계정우회·kss 자막·로고경로·SNS전채널 → 이 파일.**

---

## Omni 오디오·앵글 락 (2026-09-10 원우)
- 막을 소리: **드론·헬기·전기모터·FPV 프로펠러** (전체 앰비언트 강제 mute 아님).
- negative: `no drone sound, no helicopter sound, no propeller noise, no electric motor whine, no FPV motor`.
- bed: VO 0dB 우선. 기본 -8 → 잔향 있으면 -18 → VO 묻히면 **-25까지**.
- 조립 시 Omni에 드론/모터 트랙 있으면 그 트랙만 스트립.
- 앵글: 인접 클립·편 안에서 **같은 무빙/앵글 반복 금지**. 직전 클립과 다른 카메라 동사 지정.
