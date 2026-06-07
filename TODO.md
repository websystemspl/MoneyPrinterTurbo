# TODO

## Stage 1 — PoC lokalny

### Konfiguracja
- [ ] Skopiować `config.example.toml` → `config.toml` i uzupełnić klucze
- [ ] Wybrać providera LLM (domyślnie OpenAI, ale lepiej Claude)
- [ ] Skonfigurować TTS (domyślnie Azure lub edge-tts — bezpłatny na start)
- [ ] Skonfigurować źródło wideo (Pexels API — bezpłatny klucz)
- [ ] Uruchomić `webui.sh` lub `uv run main.py`

### Testy funkcjonalne
- [ ] Wygenerować wideo z gotowym skryptem (tryb "Script to Video")
- [ ] Przetestować tryb "Subject to Video" (LLM generuje skrypt)
- [ ] Sprawdzić jakość napisów (SRT)
- [ ] Sprawdzić dostępne głosy TTS
- [ ] Zmapować endpointy API (`/app/routers/`)

### Rozpoznanie pod SaaS
- [ ] Zrozumieć model zadań (jak silnik kolejkuje wideo)
- [ ] Sprawdzić czy jest jakaś forma auth już w kodzie
- [ ] Zidentyfikować gdzie trzymać pliki outputowe per user

## Stage 2 — Brand & Deploy
- [ ] Wybrać nazwę i domenę
- [ ] Wybrać hosting
- [ ] Przygotować docker-compose produkcyjny
- [ ] SSL + reverse proxy

## Stage 3 — SaaS
- [ ] Landing page (wireframe → impl)
- [ ] System auth użytkowników
- [ ] Dashboard: historia jobów
- [ ] Kredyty / limity per plan
- [ ] Integracja Stripe
- [ ] Admin panel (statystyki, zarządzanie userami)

## Backlog / Pomysły
- Własny model TTS (bardziej naturalny głos)
- Obsługa wielu języków w UI
- White-label (rebrand dla resellera)
- API publiczne dla integracji
