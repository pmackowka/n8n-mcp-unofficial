# Projekt: Integracja Antigravity z n8n przez MCP

Ten projekt służy jako dedykowane środowisko do zarządzania, tworzenia i edytowania przepływów pracy (workflows) w instancji **n8n** bezpośrednio z poziomu czatu **Antigravity** (IDE).

## Źródło wiedzy i dokumentacja
Projekt bazuje na oficjalnej dokumentacji serwera `n8n-mcp`:
- [ANTIGRAVITY_SETUP.md](https://github.com/czlonkowski/n8n-mcp/blob/main/docs/ANTIGRAVITY_SETUP.md)

## Co zostało skonfigurowane (Krok po kroku)

1. **Izolowane środowisko Node.js**: 
   Zamiast instalować pakiety globalnie, zainicjowaliśmy lokalny projekt (`npm init -y`) w folderze `/Users/p/Documents/dev/n8n-MCP`.
   
2. **Instalacja serwera n8n-mcp**: 
   Pobraliśmy paczkę `n8n-mcp` poleceniem `npm install n8n-mcp`. Pozwala to na uniknięcie konfliktów z innymi narzędziami w systemie operacyjnym (podobnie jak `venv` w Pythonie).

3. **Plik instrukcji dla agenta AI (`AGENTS.md`)**:
   Zgodnie z dokumentacją, utworzyliśmy plik `AGENTS.md`. Zawiera on specjalne wytyczne dla mnie (jako modelu) – zasady, według których przeszukuję szablony, sprawdzam węzły i tworzę przepływy pracy w n8n.

4. **Konfiguracja połączenia z Hostinger (`mcp_config.json`)**:
   Zaktualizowaliśmy plik `/Users/p/.gemini/antigravity/mcp_config.json`, dodając konfigurację uruchamiającą lokalnie pobrany skrypt serwera MCP (`.../node_modules/n8n-mcp/dist/mcp/index.js`).
   Dodatkowo:
   - Skonfigurowaliśmy adresy `N8N_API_URL` oraz `N8N_BASE_URL` by wskazywały na Twoją instancję: `https://n8n.srv1645572.hstgr.cloud`.
   - Zintegrowaliśmy klucz `N8N_API_KEY`.
   - Dodaliśmy flagę `"NODE_TLS_REJECT_UNAUTHORIZED": "0"`, co rozwiązuje problemy z certyfikatami SSL podpisanymi przez nieznane urzędy (co miało miejsce w przypadku infrastruktury Hostingera).

## Jak wygląda przyszła współpraca (Workflow)

Kiedy w przyszłości będziesz chciał coś zmienić lub zbudować w n8n, Twój proces pracy powinien wyglądać następująco:

1. **Otwórz ten projekt w IDE**: Uruchom środowisko w folderze `/Users/p/Documents/dev/n8n-MCP`. (Otwierając ten folder dajesz mi dostęp do pliku `AGENTS.md`, dzięki któremu "pamiętam" jak poprawnie budować flow w n8n).
2. **Zacznij rozmowę**: Po prostu opisz, jaki przepływ pracy chcesz stworzyć. Na przykład: *"Utwórz webhook, który po odebraniu danych wyśle wiadomość na Slacka."*
3. **Moje działania**: Wykorzystam narzędzia n8n, przeszukam bazę szablonów, skonfiguruję węzły i wdrożę gotowy przepływ bezpośrednio na Twój serwer n8n w Hostingerze!
