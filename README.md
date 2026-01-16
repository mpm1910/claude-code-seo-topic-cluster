# 🔗 Topic Cluster Agent for Claude Code

  **Agent SEO do automatycznego tworzenia klastrów tematycznych z słów kluczowych**

  Nowoczesny agent wykorzystujący podejście oparte na encjach, intencji wyszukiwania i semantic clustering do profesjonalnego grupowania keywords i tworzenia strategii contentu.

  ---

  ## 📋 Opis

  Topic Cluster Agent to specjalistyczny agent dla Claude Code, który analizuje eksporty słów kluczowych (Senuto/Excel) i automatycznie:

  - ✅ Grupuje keywords według **encji** (core entities)
  - ✅ Klasyfikuje **intencje wyszukiwania** (informacyjna, komercyjna, transakcyjna)
  - ✅ Tworzy **semantic clusters** na podstawie podobieństwa semantycznego
  - ✅ Mapuje **customer journey** (Query Fan-out)
  - ✅ Priorytetyzuje klastry
  - ✅ Generuje gotowy **content plan** (Pillar + Cluster Pages)

  ---

  ## 🚀 Instalacja

  ### Wymagania

  - [Claude Code CLI](https://github.com/anthropics/claude-code) (najnowsza wersja)
  - API key od Anthropic
  - Python 3.8+ (opcjonalne, dla semantic embeddings)

  ### Instalacja agenta

  1. Skopiuj plik `topic-cluster.md` do folderu agentów:
     ```bash
     # Windows
     copy topic-cluster.md %USERPROFILE%\.claude\agents\

     # macOS/Linux
     cp topic-cluster.md ~/.claude/agents/

  2. Uruchom Claude Code:
  claude
  3. Agent jest gotowy do użycia!

  ---
  📁 Struktura projektu

  Agent działa w zorganizowanej strukturze folderów:

  klienci/
  ├── klient1/
  │   ├── wsad/                    # Pliki źródłowe
  │   │   └── slowa_kluczowe.xlsx  # Export z Senuto
  │   └── klastry/                 # Outputy agenta (auto-tworzone)
  │       ├── klaster-1-nazwa.md
  │       ├── klaster-2-nazwa.md
  │       └── klastry-summary.md
  ├── klient2/
  │   └── wsad/
  ...

  ---
  🎯 Użycie

  Podstawowe użycie

  1. Umieść plik slowa_kluczowe.xlsx (export z Senuto) w folderze ./wsad/
  2. Uruchom Claude Code w folderze klienta:
  cd klienci/klient1
  claude
  3. Wydaj komendę:
  Zrób klastry tematyczne
  4. Agent automatycznie:
    - Znajdzie plik w ./wsad/
    - Przeanalizuje słowa kluczowe
    - Stworzy klastry w ./klastry/

  Zaawansowane komendy

  # Analiza słów kluczowych
  "analiza słów kluczowych"

  # Tylko klastry high priority
  "klastry high priority"

  # Rozszerzenie istniejącego klastra
  "dodaj do klastra [nazwa]"

  # Wskazanie własnej ścieżki
  "zrób klastry z pliku /sciezka/do/keywords.xlsx"

  ---
  📊 Format pliku wejściowego

  Agent oczekuje pliku Excel/CSV z kolumnami:
  ┌─────────────────────────────┬──────────────────────┬─────────────┐
  │           Kolumna           │         Opis         │  Wymagana   │
  ├─────────────────────────────┼──────────────────────┼─────────────┤
  │ Słowo kluczowe              │ Fraza keyword        │ ✅          │
  ├─────────────────────────────┼──────────────────────┼─────────────┤
  │ Śr. mies. liczba wyszukiwań │ Search volume        │ ✅          │
  ├─────────────────────────────┼──────────────────────┼─────────────┤
  │ CPC (PLN)                   │ Cost per click       │ ⚠️ Zalecana │
  ├─────────────────────────────┼──────────────────────┼─────────────┤
  │ Liczba słów kluczowych      │ Liczba słów w frazie │ ❌          │
  ├─────────────────────────────┼──────────────────────┼─────────────┤
  │ Wariacje                    │ Warianty keyword     │ ❌          │
  └─────────────────────────────┴──────────────────────┴─────────────┘
  Przykład (Senuto export):
  Słowo kluczowe,Śr. mies. liczba wyszukiwań,CPC (PLN)
  najlepsze narzędzia SEO,10000,15.50
  narzędzia SEO darmowe,5000,8.20
  porównanie narzędzi SEO,3000,12.00

  ---
  🧠 Metodologia

  Agent wykorzystuje 5-fazowy proces:

  1. Core Entity Identification

  Wyodrębnia główną encję z każdego keyword (np. "narzędzie SEO", "link building")

  2. Search Intent Classification

  Klasyfikuje intencję:
  - 🔍 Informacyjna (co, jak, dlaczego)
  - 🛒 Komercyjna (najlepszy, porównanie, ranking)
  - 💰 Transakcyjna (kup, cena, sklep)

  3. Semantic Clustering

  Grupuje keywords o podobieństwie semantycznym > 80% (embeddings)

  4. Query Fan-out Mapping

  Mapuje customer journey od awareness → purchase

  5. Prioritization

  Scoruje klastry (0-100) według:
  - Volume
  - Business intent
  - Competition (CPC)
  - Content gap

  ---
  📦 Outputy

  Agent generuje:

  1. Klastry indywidualne (klaster-{id}-{slug}.md)

  Każdy plik zawiera:
  - 📊 Metadata klastra
  - 📋 Keywords (pillar + supporting)
  - 🧭 Query Fan-out (customer journey)
  - 📝 Content Plan (Pillar + Cluster Pages)
  - 💡 Information Gain opportunities
  - 🔗 Internal linking strategy

  2. Summary (klastry-summary.md)

  Zbiorczy raport z:
  - 🎯 Executive Summary
  - 📊 Tabela wszystkich klastrów
  - ⚠️ High/Medium/Low priority breakdown
  - 📈 Aggregate statistics
  - 🎯 Implementation roadmap

  ---
  🎨 Przykład output

  # 🔗 KLASTER: Narzędzia SEO

  **Status:** ⚠️ High Priority
  **Priority Score:** 85

  ## 📊 Metadata

  | Parametr | Wartość |
  |----------|---------|
  | **Core Entity** | narzędzie SEO |
  | **Core Intent** | Komercyjna |
  | **Total Volume** | 50,000 |
  | **Keywords Count** | 45 |

  ## 📝 Content Plan

  ### Pillar Page
  **URL:** `/narzedzia-seo-kompletny-przewodnik`
  **Title:** `Narzędzia SEO - Kompletny Przewodnik 2026`
  **Word Count:** 4000 słów

  ### Cluster Page 1: Co to są narzędzia SEO
  **URL:** `/co-to-sa-narzedzia-seo`
  **Intent:** Informacyjna
  ...

  ---
  🔧 Konfiguracja

  Model

  Agent używa Claude Opus dla najlepszej jakości analizy semantycznej.

  Narzędzia

  - Read - czytanie plików Excel/CSV
  - Glob - wyszukiwanie plików
  - Grep - analiza tekstowa
  - Bash - operacje na plikach
  - Write - generowanie outputów

  Skills

  Agent wykorzystuje topic-cluster-knowledge skill z bazą wiedzy SEO.

  ---
  💡 Best Practices

  ✅ DO:

  - Używaj eksportów z Senuto/Ahrefs/SEMrush
  - Minimum 100+ keywords dla najlepszych wyników
  - Regularnie aktualizuj dane (co 3-6 miesięcy)
  - Review manual klastrów high priority

  ❌ DON'T:

  - Nie używaj keywords z volume < 10
  - Nie mieszaj języków (tylko PL lub tylko EN)
  - Nie pomijaj kolumny CPC (wpływa na prioritization)

  ---
 
  🤝 Contributing

  Znalazłeś bug lub masz pomysł na feature?

  1. Otwórz issue
  2. Opisz problem/feature
  3. Dołącz przykładowy plik keywords (jeśli relewantne)

  ---
  📄 Licencja

  MIT License - używaj jak chcesz!

  ---
  🔗 Linki

  - https://github.com/anthropics/claude-code
  - https://www.senuto.com/
  ---
