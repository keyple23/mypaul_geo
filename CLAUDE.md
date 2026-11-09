# 마이폴학교 매거진 (GEO 사이트)

이 저장소는 마이폴학교 매거진(Next.js 15, Vercel, https://news.mypaul.org)이다.
목표는 네이버 웹사이트탭과 AI 검색에서 메인 키워드 "대안학교", "국제학교" 상위노출이다.
모든 대화와 산출물은 한국어로 작성한다.

## 구조
- content/articles/{slug}.md : 글. frontmatter = title, description, category(alternative|compare|study|school), published, updated, keywords[], faq[{q,a}], draft. 주소 /articles/{slug}/
- content/keywords/*.md : 키워드 페이지(허브). frontmatter = slug, keyword, variants[], title, description, priority, articles[], faq[]. 주소 /keywords/{slug}/
  - 메인 허브: alternative.md(/keywords/대안학교/), international.md(/keywords/국제학교/), brand.md(/keywords/마이폴학교/)
- content/home.md, content/settings.json : 홈 문구, 사이트 설정·메뉴. /admin 관리자 화면에서도 GitHub 로 직접 수정된다.
- 이미 있는 것: sitemap, robots(AI 크롤러 허용), rss.xml, llms.txt, 구조화 데이터(lib). 새로 만들지 않는다.
- 템플릿: content/_글템플릿.md, content/keywords/_키워드템플릿.md
- 운영 가이드: 가이드.md

## 글 작성 규칙
- 첫 문단 3문장 안에 결론과 메인 키워드.
- H2 는 질문형 4~6개, 각 H2 첫 문장이 답.
- 표 1개 이상, 1,800~3,000자, FAQ 3~4개는 frontmatter 에.
- 내부링크: 메인 허브(/keywords/대안학교/ 또는 /keywords/국제학교/), 관련 글 1~2개, 마지막 문단에 /keywords/마이폴학교/ 1회.
- 새 글은 해당 허브 키워드 페이지 articles 목록 맨 위에 slug 추가.

## 금지
- 비유법, em dash(—, –, ㅡ), 이모티콘.
- 다른 학교 실명 비방, 확인되지 않은 수치·순위·합격 실적.
- 법·제도는 일반적인 수준으로만.
- 숨김 텍스트.
- 기존 글은 사용자 승인 없이 수정·삭제하지 않는다.

## 배포와 알림
- main 에 push 하면 Vercel 이 자동 배포한다. push 전 git pull --rebase.
- 배포 후 IndexNow 로 새 주소를 알린다.
  - 엔드포인트: https://searchadvisor.naver.com/indexnow, https://api.indexnow.org/indexnow
  - host news.mypaul.org, key 64e5d60f9d0803797620c64f22df08b9, keyLocation https://news.mypaul.org/64e5d60f9d0803797620c64f22df08b9.txt
- 월·수·금 오전에 예약 작업이 글 1편씩 자동 발행한다. 같은 주제가 겹치지 않게 기존 글 목록을 먼저 확인한다.
