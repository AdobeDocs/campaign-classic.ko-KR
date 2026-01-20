---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---
# 🚀 데모 프롬프트 - v7에서 v8 설명서 분석

**이 전체 프롬프트를 Cursor/ChatGPT에 복사하여 붙여 넣어 v7 폴더를 분석합니다**

&#x200B;---

## 📋 프롬프트(여기에서 복사) ⬇️

```markdown
# Campaign v7 Documentation Analysis

Analyze the v7 documentation folder and generate a detailed Markdown report with recommendations.

---

## CONTEXT

**v7 Repository**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/`  
**v8 Repositories**:
- `/Users/florentvignes/Documents/GitHub/campaign.en/` (Campaign v8)
- `/Users/florentvignes/Documents/GitHub/campaign-web.en/` (Campaign Web UI v8)

---

## TARGET FOLDER

**Analyze this folder**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/help/delivery/using/`

*(Replace with any folder: workflow, web, platform, reporting, etc.)*

---

## FEATURE PARITY CONTEXT

### v7-Specific Features (NOT in v8 FFDA)
- **Coupons** (personalized-coupons.md)
- **MRM** (Marketing Resource Management)
- **Surveys** (online surveys)
- **Distributed Marketing**
- **Mid-sourcing** (on-premise setup)
- **SpamAssassin** (on-premise spam filtering)
- **On-premise/Hybrid** configurations

### v8 Documentation Structure
- **Campaign Web UI**: `/campaign-web.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign-web/v8/
- **Campaign v8**: `/campaign.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/

---

## OUTPUT FORMAT

Generate a complete Markdown report with this structure:

### 1. HEADER & SUMMARY
\`\`\`markdown
# 📊 v7 [Folder Name] Analysis

**Folder**: `/help/[folder]/using/`  
**Generated**: [Date]  
**Total Files**: [X]

## 📈 Summary

| Metric | Count | Percentage |
|--------|-------|------------|
| 📄 Total Files | X | 100% |
| ✅ KEEP | X | X% |
| 🗑️ DELETE | X | X% |
| ➡️ MOVE | X | X% |
| 🔍 REVIEW | X | X% |
\`\`\`

### 2. FILE-BY-FILE ANALYSIS TABLE
\`\`\`markdown
## 📋 Complete File Analysis

### [Category Name] (X files)

| # | v7 File | v8 Match | Match % | Notes | Action |
|---|---------|----------|---------|-------|--------|
| 1 | filename.md | [v8 link](https://...) | 95% | Fully in v8 | 🗑️ DELETE |
| 2 | **filename.md** | NONE | 0% | **v7-specific** | ✅ **KEEP** |
| 3 | filename.md | [v8 link](https://...) | 70% | Migrate tips | ➡️ MOVE |

[Repeat for each category: Get Started, Email, SMS, etc.]
\`\`\`

### 3. MUST KEEP SECTION
\`\`\`markdown
## ✅ Must Keep - v7-Specific Features

| File | Reason | Badge Text |
|------|--------|------------|
| filename.md | Feature not in v8 FFDA | "This feature is not available..." |
\`\`\`

### 4. QUICK WINS SECTION
\`\`\`markdown
## 🗑️ Quick Wins - Safe to Delete Now

**[Category]** (X files):
- ✅ filename.md → 95% in v8/path
- ✅ filename.md → 90% in v8/path
\`\`\`

### 5. MIGRATION SECTION
\`\`\`markdown
## ➡️ Content to Migrate First

| v7 File | v8 Destination | Content to Migrate | Effort |
|---------|----------------|-------------------|--------|
| filename.md | /v8/path.md | Sections X, Y, Z | 2 hours |
\`\`\`

### 6. EXECUTION PLAN
\`\`\`markdown
## 🎯 Execution Plan

### Week 1: Quick Deletions
- [ ] Delete [category] files (X)
- [ ] Delete [category] files (X)
**Total**: X files deleted

### Week 2: Badging
- [ ] Badge v7-specific files (X)

### Week 3: Review
- [ ] Review partial matches (X)
\`\`\`

---

## ANALYSIS RULES

### For Each File, Determine:

1. **Match Percentage**:
   - 95-100% = Fully covered in v8 → DELETE
   - 70-90% = Mostly covered, check gaps → DELETE or MOVE
   - 40-70% = Partial coverage → REVIEW
   - 0-40% = Not in v8 → KEEP or REVIEW

2. **v7-Specific Indicators** (→ KEEP):
   - Mentions "on-premise", "hybrid", "mid-sourcing"
   - Coupons, MRM, Surveys, Distributed Marketing
   - SpamAssassin, nlserver configuration
   - Client Console specific features
   - Database schema/structure docs

3. **DELETE Criteria**:
   - Basic features (email, SMS, push creation)
   - Standard workflow activities (query, split, enrichment)
   - Common reports
   - Channel basics fully documented in v8

4. **MOVE Criteria**:
   - Troubleshooting tips not in v8
   - Best practices missing in v8
   - Advanced patterns useful for v8
   - Good examples/use cases

5. **REVIEW Criteria**:
   - Partial v8 coverage (50-70%)
   - Unclear if feature exists in v8
   - Complex mixed content

---

## IMPORTANT

- **Organize by category** (Get Started, Email, SMS, Push, etc.)
- **Include Experience League URLs** for v8 matches
- **Bold v7-specific files** that must be kept
- **Estimate match percentage** for each file
- **Provide clear reasoning** for each decision
- **Include effort estimates** for migrations

---

Generate the complete Markdown report now.
```

&#x200B;---

## 🎯 데모 지침

### 1단계: 프롬프트 표시1. 이 파일(`DEMO-PROMPT-STANDALONE.md`) 열기2. &quot;프롬프트&quot; 섹션으로 스크롤3. 설명: *&quot;자동 분석 프롬프트&quot;*

### 2단계: 프롬프트 복사1. &quot;# Campaign v7 설명서 분석&quot;에서 끝까지 모두 선택2. 클립보드에 복사3. 메시지: *&quot;전체 메시지를 복사하는 중입니다...&quot;*

### 3단계: 붙여넣기 및 실행1. 커서 열기2. 프롬프트 붙여넣기3. 설명: *&quot;...커서 &quot;*&quot;에 붙여 넣기4. 히트 Enter

### 4단계: 결과 표시1. 생성 대기(~30-60초)2. 생성된 보고서를 스크롤합니다3. 주요 섹션 강조 표시:   - 📊 요약 통계   - 📋 파일별 테이블   - ✅은(는) 섹션을 유지해야 합니다.   - 🗑️개의 빠른 성공   - 🎯 실행 계획

### 5단계: 와 모멘트1. Markdown 미리 보기 표시2. 다음을 지적합니다.   - *&quot;111개 파일이 자동으로 분석됨&quot;*   - *&quot;67개 파일을 안전하게 삭제할 수 있음(60% 감소)&quot;*   - *&quot;18개의 v7 관련 파일이 식별됨&quot;*   - *&quot;타임라인이 있는 실행 계획 완료&quot;*

&#x200B;---

## 💡 데모 팁

### 대화형으로 만들기&#x200B;**대상자에게 묻기**: *&quot;분석할 폴더는 무엇입니까?&quot;*- 게재 ✅(111개 파일 - 추천)- 워크플로우 ✅(121개 파일 - 더 큼)- 웹 ✅(26개 파일 - 빠른 데모)- ✅ 보고 중(32개 파일 - 빠름)

### 즉석으로 맞춤화&#x200B;**유연성 표시**: 프롬프트에서 폴더 경로를 변경합니다.

```
/help/workflow/using/  → Analyze workflows
/help/web/using/       → Analyze web apps
/help/platform/using/  → Analyze platform
```

### 주요 기능 강조 표시1. **자동화**: *&quot;수동 작업 필요 없음&quot;*2. **정확도**: *&quot;비교를 위해 v8 설명서를 사용&quot;*3. **실행 가능**: *&quot;확인란이 있는 실행 준비 계획&quot;*4. **스마트**: *&quot;v7별 기능을 자동으로 식별합니다&quot;*

### 시간 비교&#x200B;**이전**: *&quot;수동 분석 = 폴더당 2~3일&quot;*\**이후**: *&quot;자동화된 분석 = 폴더당 30초&quot;*

**ROI**: *&quot;21개 폴더 × 2일 = 42일 → 15분&quot;*

&#x200B;---

## 📊 예상 출력 미리 보기

```markdown
# 📊 v7 Delivery Analysis

**Total Files**: 111

## 📈 Summary
| Metric | Count | Percentage |
|--------|-------|------------|
| ✅ KEEP | 18 | 16% |
| 🗑️ DELETE | 67 | 60% |
| ➡️ MOVE | 8 | 7% |
| 🔍 REVIEW | 18 | 17% |

## 📋 File Analysis

### 📧 Email (18 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | 🗑️ DELETE |
| 2 | creating-an-email-delivery.md | campaign-web/v8/email/create | 95% | 🗑️ DELETE |

### 📱 SMS (7 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | sms-channel.md | campaign-web/v8/msg/send-sms | 90% | 🗑️ DELETE |
| 2 | **sms-set-up-mid.md** | NONE | 0% | ✅ **KEEP** |

[... continues for all categories ...]

## ✅ Must Keep (18 files)
- **personalized-coupons.md** - Coupons not in v8 FFDA
- **sms-set-up-mid.md** - Mid-sourcing (on-prem)
- **spamassassin.md** - On-prem spam filtering

## 🗑️ Quick Wins (67 files)
Email basics, SMS, Push, Direct mail → All in v8

## 🎯 Execution Plan
Week 1: Delete 67 files (60%)
Week 2: Badge 18 files
Week 3: Review 18 files
```

&#x200B;---

## 🎬 데모 스크립트

**열기**:
> &quot;오늘은 AI를 사용하여 v7 설명서를 자동화하는 방법을 보여 드리겠습니다. 전에는 몇 주가 걸렸는데 지금은 몇 분이 걸립니다.&quot;

**문제**:
> &quot;1,500개 이상의 v7 설명서 파일이 있습니다. 많은 항목이 v8에서 중복됩니다. 보관, 삭제 또는 마이그레이션할 항목을 확인해야 합니다.&quot;

**솔루션**:
> &quot;모든 폴더를 분석하고 실행 가능한 권장 사항을 생성하는 스마트 프롬프트를 만들었습니다.&quot;

**데모**:
> &quot;제가 보여드리죠. 111개 파일로 &#39;게재&#39; 폴더를 분석하겠습니다...&quot;
> 
> [프롬프트 복사, 붙여넣기, 실행]
> 
> 30초 후에 완전한 분석을 할 수 있습니다.&quot;

**결과**:
> &quot;이 항목을 보십시오.
> - 삭제할 파일 67개(60% 감소)
> - v7별 파일 18개 식별됨
> - 마이그레이션할 파일 8개
> - 3주 실행 계획 완료
> 
> 모두 자동화되었습니다. 모두 정확합니다.&quot;

**닫기**:
> &quot;21개 폴더 모두에 대해 동일한 프로세스가 작동합니다. 6주가 걸리던 것이 지금은 15분이 걸린다.&quot;

&#x200B;---

## 🚀 데모 준비 완료!

**추가**:
1. 이 파일 열기
2. 프롬프트 복사
3. 커서에 붙여넣기
4. 매직 ✨ 표시

**총 데모 시간**: 3~5분\
**Wow 요소**: 🔥🔥🔥

