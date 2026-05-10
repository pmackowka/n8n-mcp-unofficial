# Projekt: Integracja Antigravity z n8n przez n8n-MCP-unofficial

Ten projekt służy jako dedykowane środowisko do zarządzania, tworzenia i edytowania przepływów pracy (workflows) w instancji **n8n** bezpośrednio z poziomu czatu **Antigravity** (IDE).

---

## Prompt na start każdej sesji (kopiuj i wklej do czatu)

```
Przed rozpoczęciem pracy z n8n:

1. Przeczytaj cały plik AGENTS.md — to są główne instrukcje jak budować workflow.
2. Znajdujesz się w projekcie n8n-MCP-unofficial — instancja n8n na Hostinger: https://n8n.srv1645572.hstgr.cloud
3. W .opencode/skills/ masz 7 lokalnych skilli n8n — używaj ich gdy potrzebujesz wiedzy o:
   - składni wyrażeń n8n (n8n-expression-syntax)
   - używaniu narzędzi MCP (n8n-mcp-tools-expert)
   - wzorcach workflow (n8n-workflow-patterns)
   - walidacji i błędach (n8n-validation-expert)
   - konfiguracji node'ów (n8n-node-configuration)
   - kodzie JavaScript w Code node (n8n-code-javascript)
   - kodzie Python w Code node (n8n-code-python)
4. W docs/workflow-diff-examples.md znajdziesz referencję do operacji diff — używaj ich do oszczędzania tokenów przy edycji workflow.
```

---

## Źródło wiedzy i dokumentacja
- Główny projekt: [czlonkowski/n8n-mcp](https://github.com/czlonkowski/n8n-mcp) na GitHub
- Antigravity setup: [ANTIGRAVITY_SETUP.md](https://github.com/czlonkowski/n8n-mcp/blob/main/docs/ANTIGRAVITY_SETUP.md)
- Skille n8n (autor: Romuald Członkowski): [czlonkowski/n8n-skills](https://github.com/czlonkowski/n8n-skills)

## Lokalne zasoby w projekcie

| Zasób | Ścieżka | Opis |
|-------|---------|------|
| Instrukcje dla modelu | `AGENTS.md` | Główne wytyczne — workflow, walidacja, batch operacje |
| 7 skilli n8n | `.opencode/skills/` | Wiedza ekspercka: składnia, wzorce, walidacja, konfiguracja |
| Referencja diff | `docs/workflow-diff-examples.md` | Przykłady oszczędnych operacji diff (oszczędność tokenów) |
| Rejestr workflow | `TEMPLATES.md` | Lista wszystkich workflowów na instancji Hostinger |

## Co zostało skonfigurowane (Krok po kroku)

1. **Izolowane środowisko Node.js**: 
   Zamiast instalować pakiety globalnie, zainicjowaliśmy lokalny projekt (`npm init -y`) w folderze `/Users/p/Documents/dev/n8n-MCP-unofficial`.
   
2. **Instalacja serwera n8n-mcp**: 
   Pobraliśmy paczkę `n8n-mcp` poleceniem `npm install n8n-mcp`. Pozwala to na uniknięcie konfliktów z innymi narzędziami w systemie operacyjnym (podobnie jak `venv` w Pythonie).

3. **Plik instrukcji dla agenta AI (`AGENTS.md`)**:
   Zgodnie z dokumentacją, utworzyliśmy plik `AGENTS.md`. Zawiera on specjalne wytyczne dla mnie (jako modelu) – zasady, według których przeszukuję szablony, sprawdzam węzły i tworzę przepływy pracy w n8n.

4. **Konfiguracja MCP w projekcie**:
   Konfiguracja serwera MCP została przeniesiona z globalnej (`~/.gemini/antigravity/`) do wnętrza projektu. Dostępne są dwa pliki konfiguracyjne:
   
   - **`opencode.json`** — dla narzędzia OpenCode (w korzeniu projektu)
   - **`.gemini/antigravity/mcp_config.json`** — dla IDE Antigravity
   
   Dzięki temu:
   - Narzędzia MCP są dostępne **tylko** gdy pracujesz w tym projekcie — inne projekty nie mają dostępu do n8n API.
   - Klucz API nie jest globalnie dostępny dla wszystkich sesji IDE.
   - Wszystko co potrzebne do n8n jest w jednym miejscu (MCP + skille + AGENTS.md).
   
   Konfiguracja zawiera:
   - Adresy `N8N_API_URL` oraz `N8N_BASE_URL` wskazujące na instancję: `https://n8n.srv1645572.hstgr.cloud`.
   - Klucz `N8N_API_KEY`.
   - Flagę `"NODE_TLS_REJECT_UNAUTHORIZED": "0"` (certyfikaty SSL Hostingera).
   
   Oba pliki konfiguracyjne są dodane do `.gitignore` — nie trafią do repozytorium.

## Jak wygląda przyszła współpraca (Workflow)

Kiedy w przyszłości będziesz chciał coś zmienić lub zbudować w n8n, Twój proces pracy powinien wyglądać następująco:

1. **Otwórz ten projekt w IDE**: Uruchom środowisko w folderze `/Users/p/Documents/dev/n8n-MCP-unofficial`. (Otwierając ten folder dajesz mi dostęp do pliku `AGENTS.md`, dzięki któremu "pamiętam" jak poprawnie budować flow w n8n).
2. **Zacznij rozmowę**: Po prostu opisz, jaki przepływ pracy chcesz stworzyć. Na przykład: *"Utwórz webhook, który po odebraniu danych wyśle wiadomość na Slacka."*
3. **Moje działania**: Wykorzystam narzędzia n8n, przeszukam bazę szablonów, skonfiguruję węzły i wdrożę gotowy przepływ bezpośrednio na Twój serwer n8n w Hostingerze!
