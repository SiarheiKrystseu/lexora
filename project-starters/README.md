# Lexora — Claude Project (opcjonalna nakładka na Skill)

Ten folder NIE jest częścią skilla — to opcjonalny dodatek, jeśli chcesz,
aby użytkownicy widzieli gotowe pytania startowe na głównej stronie
projektu w claude.ai. Sam Skill (`SKILL.md` + `references/`) działa
niezależnie od tego i nie wymaga Projektu, żeby się uruchamiać.

## Jak to połączyć

1. Zainstaluj skill `lexora-legal-skill` zgodnie z głównym README (Settings
   → Capabilities → Skills → Upload skill). To wystarczy, żeby Lexora
   odpowiadała poprawnie w KAŻDYM czacie, nie tylko w Projekcie.
2. (Opcjonalnie, jeśli chcesz "landing page" z gotowymi pytaniami) Utwórz
   nowy **Project** w claude.ai → nazwij go np. "Lexora — Konsultant
   Prawny".
3. W polu opisu Projektu wklej treść z `description.md` poniżej.
4. W sekcji "Conversation starters" Projektu dodaj pytania z
   `conversation-starters.md` poniżej — każde jako osobny starter.
5. Pole "Custom instructions" Projektu możesz zostawić **puste** albo
   wpisać jedno zdanie: "Odpowiadaj jako Lexora, korzystając z dostępnego
   skilla dot. prawa medycznego w Polsce." — cała właściwa logika i tak
   pochodzi ze Skilla, więc nie trzeba duplikować treści.

## Ograniczenie
Conversation starters działają tylko wewnątrz danego Projektu — nie
pojawią się w zwykłym nowym czacie poza Projektem. Jeśli chcesz, aby
każdy nowy użytkownik widział je od razu "na głównej", musisz skierować go
do linku tego konkretnego Projektu (Project jest widoczny tylko dla
Twojego konta, chyba że jest to Project współdzielony w ramach Team/
Enterprise — wtedy administrator może go udostępnić członkom organizacji).
