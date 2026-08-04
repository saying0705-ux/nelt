# NELT × 사월이네공부방 판매 제휴 제안서

사월이네공부방 대표님 열람용 단일 페이지 제안서입니다. 정적 파일만 사용하므로 빌드 설정 없이 그대로 배포됩니다.

## 구성

```
index.html              제안서 본문 (단일 페이지)
pdf/                    열람·다운로드용 원본 PDF 9종
  grammar-level2~7.pdf    문법 실전 모의고사 미리보기 6권
  report-summary.pdf      요약 성적표 샘플
  report-detail.pdf       상세 성적표 샘플
  report-cumulative.pdf   누적 성적표 샘플
thumb/                  각 PDF 1페이지 표지 썸네일 (자동 생성)
```

## 배포

```bash
git init
git add .
git commit -m "NELT 사월이네공부방 제안서"
git remote add origin https://github.com/<계정>/<저장소>.git
git push -u origin main
```

Vercel → Add New Project → 해당 저장소 선택 → Framework Preset은 **Other**, Build Command와 Output Directory는 비워 둔 채 Deploy.

## 동작 방식

- 표지 이미지나 `열어보기`를 누르면 모달에서 PDF가 바로 열립니다.
- `저장`을 누르면 한글 파일명으로 다운로드됩니다.
- 화면 폭 720px 미만이거나 iOS·Android 기기에서는 모달 대신 새 탭으로 엽니다. (모바일 브라우저의 iframe PDF 미리보기 제약 회피)
- `<meta name="robots" content="noindex">`가 적용되어 검색엔진에 노출되지 않습니다.

## 수정이 잦은 값

| 항목 | 위치 |
|---|---|
| 수수료 10% | `#summary` 요약표, `#settle` 수수료 카드 |
| 응시권 가격 | `#product` 내 `.prices` |
| 카카오톡 아이디 | `#next` 회신 카드, 다음 단계 2번 |
| 담당자명 | 요약표 · `#settle` · footer |

## 자료 교체

PDF를 바꾸면 썸네일도 다시 만들어야 합니다.

```bash
pdftoppm -jpeg -r 45 -f 1 -l 1 -jpegopt quality=78 pdf/grammar-level2.pdf thumb/grammar-level2
mv thumb/grammar-level2-01.jpg thumb/grammar-level2.jpg
```
