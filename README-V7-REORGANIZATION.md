---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---
# 📚 v7 설명서 재구성 키트

**2 프롬프트 pour analyzer et réorganizer la doc v7 → v8**

&#x200B;---

## 📁개의 Fichiers

### 🔍개 프롬프트(지침)

| 피셔 | 설명 | 출력 |
|---------|-------------|--------|
| `PROMPT-1-OVERVIEW-ALL-FOLDERS.md` | Vue d&#39;ensemble de TOUS les folders v7 | `v7-reorganization-overview.md` |
| `PROMPT-2-DETAILED-FOLDER.md` | DÉTAILLÉE d&#39;UN 폴더 비교 % 일치 분석 | `[folder]-detailed-analysis.md` |

&#x200B;---

## 🚀 사용률

### ⃣ 1️ Vue d&#39;Ensemble (tous les folders)

```bash
# 1. Ouvrir le prompt
open PROMPT-1-OVERVIEW-ALL-FOLDERS.md

# 2. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 3. Coller dans Cursor/ChatGPT
# 4. Obtenir : v7-reorganization-overview.md
```

**Génère**:
- 📊 실행 요약(통계 전역)
- 📁 des 21개 폴더 분석
- 🎯 메트릭 비우선 순위
- ✅개 작업 항목
- ⚠️ Risques
- 📈 Métriques

**맞춤** : ~50~60페이지 Markdown

&#x200B;---

### ⃣ 2️ Détaillée d&#39;un 폴더 분석

```bash
# 1. Ouvrir le prompt
open PROMPT-2-DETAILED-FOLDER.md

# 2. Modifier la ligne :
📁 **Analyze**: /Users/.../help/delivery/using/

# 3. Remplacer par le folder souhaité :
# - /help/delivery/using/
# - /help/workflow/using/
# - /help/web/using/
# - etc.

# 4. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 5. Coller dans Cursor/ChatGPT
# 6. Obtenir : [folder]-detailed-analysis.md
```

**Génère**:
- 📊 Stats du 폴더
- 📋 타블로 데탈레 오르가니제 comme Experience League
- 🔗 Liens cliquables(v7 + Experience League)
- 📈 Jusqu&#39;à 3 일치 v8 par fichier avec %
- 📄 파일 조각 파일 다시 캡처
- 🎯 조직 구성 계획
- ✅개의 확인란에 추적 추가

**맞춤** : ~30~40페이지 Markdown

&#x200B;---

## 📊 Example d&#39;Output

### 프롬프트 1(개요)

```markdown
# 📊 v7 Documentation Reorganization Overview

**Total Files**: 1,500
**KEEP**: 400 (27%)
**DELETE**: 800 (53%)
**MOVE**: 200 (13%)
**REVIEW**: 100 (7%)

## 📁 Folder Analysis

### 🟢 100% KEEP - v7-Only Content
| Folder | Files | Reason |
|--------|-------|--------|
| /installation/ | 75 | On-premise setup |
| /mrm/ | 5 | Not in v8 FFDA |
...
```

### 프롬프트 2 (세부 폴더)

```markdown
# 📊 v7 Folder Analysis: Delivery

**Total Files**: 111

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | Notes | Action |
|---|---------|------------|---|------------|---|-------|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | - | - | Fully in v8 | 🗑️ DELETE |
| 9 | sms-set-up-mid.md | NONE | 0% | - | - | Mid-sourcing (on-prem) | ✅ KEEP |
...
```

&#x200B;---

## 🎯 워크플로 재명령

### 세메인 1 : 뷰 디&#39;앙상블1. **프롬프트 1** → 옵테니어 `v7-reorganization-overview.md` 실행2. 식별자 및 폴더 우선 순위3. Partager avec 이해 당사자

### Semine 2-4 : 분석 détaillée1. Chaque 폴더 우선 순위 게시 :   - **프롬프트 2** 실행   - 개체 `[folder]-detailed-analysis.md`   - 발리데르 레 데시옹   - 시작자 작업

### Semine 5+ : Execution1. Supprimer les fichiers identifiés (DELETE)2. Badger les fichiers v7-only (KEEP)3. Migrer le contenu manquant (MOVE)4. 검토자 les cas ambigus (REVIEW)

&#x200B;---

## 💡개 팁

### 프롬프트 쏟기- ✅ 복사기/복사기 l&#39;intégralité du 프롬프트- ✅ 새 pas 수정자 le 형식- ✅ 어댑터 도구 모음 스키마 du 폴더(프롬프트 2)

### 출력 쏟기- 📝 출력 en Markdown(pas HTML)- 🔗 Liens cliquables automatiques- ✅개의 확인란에 추적 추가- 📊 통계 및 시간 제한- 🎨 이모티콘 항목

### 분석 후- 🎯 Commencer par les gros 폴더(게재, 워크플로)- ⚡ Prioriser les quick wins(95-100% 일치)- 🔍 검토자 설명서 les cas ambigus(&lt;70% 일치)- ✅ 유효성 검사기 SME 상대 억제 대량

&#x200B;---

## ⚠️ 중요

### 아방트 드 수프라페르1. ✅ Vérifier l&#39;equivalid v82. ✅ Vérifier qu&#39;il n&#39;y a pas de contenu v7별3. ✅ 메타트르 `redirects.csv`4. ✅ 유효성 검사기 AVEC UN 전문가(푸어 레 프리미어)

### Pour les fichiers v7-only1. ✅ Ajouter un badge au début du fichier2. ✅ Expliquer pourqui c&#39;est v7 전용3. ✅ 제한 기간 제한 없음 v8

&#x200B;---

## 🆘 지원

**질문** ?
- Prompt ne fonctionne pas → Vérifier les chemins des repos
- Output trop long → Demander un 이력서
- 베소인데비르 → 핑레퀴페 독

&#x200B;---

**Dernière mise à jour** : 2026-01-13

