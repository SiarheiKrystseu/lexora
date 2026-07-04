# Lexora — AI Legal Assistant for Healthcare

![Lexora logo](assets/lexora-logo.jpeg)

**Lexora** to Agent Skill dla Claude pełniący rolę asystenta prawnego dla
lekarzy wykonujących zawód w Polsce. Wersja 2.0 — rozszerzona o drzewa
decyzyjne, checklisty, szablony pism, system oceny ryzyka i moduły
specjalistyczne (pediatria, psychiatria, medycyna pracy).

## Instalacja (claude.ai)

1. Pobierz to repozytorium jako ZIP (`Code → Download ZIP` na GitHub) albo
   sklonuj: `git clone <adres-repo>`.
2. W claude.ai wejdź w **Settings → Capabilities → Skills → Upload skill**.
3. Wskaż folder/zip `lexora-legal-skill/` (musi zawierać `SKILL.md` w
   katalogu głównym).
4. Gotowe — Lexora sama włączy się, gdy rozmowa dotyczy prawa medycznego w
   Polsce (dokumentacja, zgody, tajemnica lekarska, RODO, NFZ,
   odpowiedzialność, raportowanie itd.). Włącz też **web search**, aby
   asystent mógł zweryfikować najnowsze zmiany w przepisach.

## Aktualizacje

Claude.ai nie synchronizuje się automatycznie z GitHub — każda aktualizacja
wymaga ponownego wgrania skilla:
1. Zaktualizuj pliki w repo i oznacz nowy release/tag (np. `v2.1`).
2. Użytkownicy pobierają nową wersję ZIP i podmieniają istniejący skill w
   Settings → Skills (usuń starą wersję, wgraj nową).

> Jeśli w przyszłości przeniesiesz część użytkowników na Claude Code,
> możesz opublikować ten sam skill przez plugin marketplace — wtedy
> aktualizacje pobierają się komendą `/plugin update` bezpośrednio z tego
> repozytorium, bez ręcznego pobierania ZIP-a.

## Pytania startowe widoczne "na głównej stronie" (opcjonalnie)

Sam Skill nie ma żadnego UI ani listy pytań startowych — uruchamia się
niewidocznie, gdy Claude uzna pytanie za związane z prawem medycznym.
Jeśli chcesz, aby użytkownicy widzieli gotowe, klikalne pytania od razu po
otwarciu czatu, potrzebny jest dodatkowo **Claude Project** — to jedyne
miejsce w Claude, gdzie taka funkcja ("conversation starters") istnieje.
Instrukcja połączenia obu elementów: `project-starters/README.md`.

## Struktura repozytorium

```
lexora-legal-skill/
├── SKILL.md                              # rola, workflow, ograniczenia, mapa referencji
├── assets/
│   └── lexora-logo.jpeg
├── project-starters/                     # opcjonalna nakładka: Claude Project + starter questions
│   ├── README.md
│   ├── description.md
│   └── conversation-starters.md
└── references/
    ├── wiarygodne-zrodla.md              # hierarchia źródeł + strategia wyszukiwania
    ├── ustawa-o-policji.md               # wstęp Policji do placówek medycznych
    ├── zawod-lekarza-tajemnica.md        # tajemnica lekarska, art. 266 KK
    ├── prawa-pacjenta-dokumentacja.md    # udostępnianie dokumentacji, terminy
    ├── zgoda-pacjenta.md                 # zgoda na zabieg, małoletni, stany nagłe
    ├── rodo-ochrona-zdrowia.md           # RODO, w tym żądanie usunięcia danych
    ├── odpowiedzialnosc-i-ryzyko.md      # odpowiedzialność prawna + system ryzyka
    ├── nfz-i-raportowanie.md             # relacje z NFZ, choroby zakaźne, NOP
    ├── moduly-specjalistyczne.md         # pediatria, psychiatria, medycyna pracy
    └── szablony-i-checklisty.md          # wzory pism i checklisty
```

`SKILL.md` zawiera tylko rolę, workflow (5 kroków) i mapę odnośników do
`references/` — dzięki temu Lexora wczytuje tylko to, co potrzebne do
danego pytania, zamiast całej wiedzy naraz (progresywne ładowanie
kontekstu, zgodnie ze standardem Agent Skills).

## Ograniczenia

- Aktywacja skilla zależy od oceny trafności przez Claude na podstawie pola
  `description` w `SKILL.md` — nie jest to sztywno "zawsze aktywny system
  prompt" jak w Claude Project. Dla tej dziedziny działa to w praktyce
  niezawodnie, bo temat jest dość wyraźnie rozpoznawalny.
- Brak wymuszonego ograniczenia wyszukiwania wyłącznie do domen urzędowych
  (to wymagałoby integracji przez Claude API z parametrem
  `allowed_domains`).
- Lexora nie zastępuje porady radcy prawnego/adwokata — patrz sekcja
  "Ograniczenia" w `SKILL.md`.

## Licencja

Dopisz plik `LICENSE` według własnego wyboru (np. MIT lub CC-BY-4.0) przed
publikacją repozytorium.
