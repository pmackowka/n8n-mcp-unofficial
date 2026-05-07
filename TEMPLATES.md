# Rejestr szablonów n8n

Plik śledzący wszystkie workflowy załadowane na instancję n8n na Hostingerze (`https://n8n.srv1645572.hstgr.cloud`).

---

## Szablony

| # | Nazwa szablonu | ID w n8n | Cel / korzyść | Wymagane kredencjały | Kolejne kroki konfiguracji | Data dodania |
|---|---|---|---|---|---|---|
| 1 | **Query GA4 data with Google Gemini AI in a Slack channel** | `b6dM5vmG0oZ0z8sh` | Zadawanie pytań o dane GA4 w języku naturalnym przez Slacka. AI agent tłumaczy pytania na metryki GA4 i odpowiada bezpośrednio w wątku. | Slack API, Google Analytics OAuth2, Google Gemini (AI Studio) | 1. Skonfiguruj kredencjały: Slack (bot token), Google Analytics OAuth2, Google Gemini API<br>2. Ustaw kanał Slack w `Slack Trigger` (channelId)<br>3. Ustaw Property ID GA4 w `Get a report in Google Analytics`<br>4. Aktywuj workflow | 2026-05-07 |

---

## Zmiany

| Data | Opis |
|---|---|
| 2026-05-07 | Utworzono plik. Dodano szablon #1: Query GA4 with Gemini in Slack |

---

**Źródło szablonu:** https://n8n.io/workflows/13038-query-ga4-data-with-google-gemini-ai-in-a-slack-channel/
**Autor:** scalo-labs
