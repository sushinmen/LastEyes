# 제3의 눈 · THIRD EYE

> An interactive narrative experience inspired by the manga **Homunculus**.
> 만화 《호문쿨루스》에서 영감을 받은 인터랙티브 픽션.
>
> **웹인터랙션디자인 / Web Interaction Design — Final Project**

A single-page, choice-based web experience. A stranger offers to open your
"third eye." If you accept, you walk through a city and *see the true shape*
hidden beneath people's surfaces — and finally, your own. Three endings.

Built with **vanilla HTML / CSS / JavaScript + GSAP**. No build step, no
framework. Just open it.

---

## ▶ 실행 / Run

**가장 쉬운 방법 (Easiest):** `index.html` 더블클릭.
(인터넷 연결 시 GSAP·폰트가 CDN에서 로드됩니다.)

**권장 (Recommended) — 로컬 서버로 실행:**

```bash
# Python
python3 -m http.server 8000
# 그다음 브라우저에서 http://localhost:8000

# 또는 Node
npx serve .
```

소리(▶ SOUND)를 켜면 생성형 앰비언트와 심장박동이 더해져 몰입감이 커집니다.
Turn on **SOUND** (top-right) for generated ambient drone + heartbeat.

---

## 🎮 조작 / Controls

| 입력 | 동작 |
|------|------|
| 클릭 / Click | 선택지 고르기 · 타이핑 즉시 완료 |
| `1` `2` `3` | 선택지 번호로 고르기 |
| `Enter` / `Space` | 타이핑 건너뛰기 |
| `Esc` | 이전 장면으로 (BACK) |

---

## 🗂 구조 / Structure

```
Third-Eye/
├── index.html        # 뼈대: 프리로더, 커서, 오버레이, 무대(stage)
├── css/style.css     # 전체 스타일 (Homunculus 다크 무드)
├── js/
│   ├── story.js      # ★ 이야기 데이터 (장면·대사·선택지) — 여기만 고치면 됨
│   └── main.js       # 엔진: 장면 렌더, 타이프라이터, 전환, 사운드, 비주얼
├── assets/           # (선택) 직접 만든 이미지 → README 참고
└── vendor/           # (선택) 오프라인용 GSAP → fetch-libs.sh
```

### ✍️ 이야기 고치기 / Editing the story
모든 텍스트·분기·선택지는 **`js/story.js`** 한 파일에 있습니다.
장면을 추가하려면 객체 하나를 더 넣고, 선택지의 `to:` 로 연결만 하면 됩니다.
한국어(`ko`)·영어(`en`)가 나란히 들어 있어 번역·수정이 쉽습니다.

### 🖼 이미지 넣기 / Adding images
기본은 코드로 그린 SVG입니다. 실제 그림을 쓰려면 `assets/README.md` 참고 —
장면에 `image: "assets/파일.jpg"` 한 줄만 추가하면 됩니다.

---

## 🎨 인터랙션 / Interaction design notes

이 프로젝트가 보여주는 인터랙션 요소들:

- **커스텀 커서** — 링이 지연 추적하고, 선택지 위에서 확대되며 라벨 표시
- **타이프라이터 대사** — 글자 단위 출력, 강조어 자동 하이라이트, 클릭 시 즉시 완료
- **장면 전환 효과** — 글리치 디스토션, 화이트 플래시(트레퍼네이션)
- **생성형 사운드** — WebAudio로 드론·심장박동을 실시간 합성 (음원 파일 없음)
- **분기 & 상태** — 방문한 장면을 기억해 거리(street)의 텍스트·선택지가 변함
- **심층(DEPTH) 미터** — 이야기가 깊어질수록 차오르고 사운드 긴장도 상승
- **코드로 그린 비주얼** — 인물·드릴·눈·지폐·실·거울 등 장면별 SVG 아트
- **접근성** — 키보드 조작, 포커스 표시, `prefers-reduced-motion` 대응
- **반응형** — 모바일에서는 커스텀 커서·과한 모션을 자동으로 줄임
- **그레이스풀 디그레이데이션** — GSAP가 없어도 모든 내용이 정상 표시됨

---

## 🔌 오프라인 / Offline

발표장에 인터넷이 없을 수 있으니, 미리 GSAP를 로컬에 받아두세요:

```bash
bash vendor/fetch-libs.sh
```

`index.html` 은 `vendor/gsap.min.js` 가 있으면 그것을, 없으면 CDN을
자동으로 사용합니다. (폰트도 오프라인이면 시스템 명조/모노로 대체됩니다.)

---

## 🙇 크레딧 / Credits

- Concept & story: 호문쿨루스(山本英夫)에서 영감 — *inspired by Hideo Yamamoto's «Homunculus»*.
- Fonts: Noto Serif KR, Space Mono (Google Fonts).
- Animation: GSAP (optional).
