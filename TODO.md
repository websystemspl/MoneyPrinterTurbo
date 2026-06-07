# TODO

## Stage 1 — PoC lokalny ✓ ZAKOŃCZONY (2026-06-07)

### Konfiguracja ✓
- [x] Skopiować `config.example.toml` → `config.toml` i uzupełnić klucze
- [x] Skonfigurować TTS (edge_tts — działa bez klucza)
- [x] Skonfigurować źródło wideo (Pexels API)
- [x] Uruchomić WebUI (`PATH="$HOME/.local/bin:$PATH" ./webui.sh`)

### Testy funkcjonalne ✓
- [x] Wygenerować pierwsze wideo (Subject to Video, EN, ~148s, 52 klipy)
- [x] TTS edge_tts działa
- [x] Pexels pobiera klipy poprawnie
- [x] GPT-4o-mini generuje skrypt

### Do dopracowania w ramach Stage 1
- [ ] Rozważyć Claude zamiast GPT-4o-mini jako LLM (litellm provider)
- [ ] Zmapować endpointy API (`/app/routers/`) pod kątem SaaS
- [ ] Sprawdzić czy jest jakaś forma auth już w kodzie
- [ ] Zidentyfikować gdzie trzymać pliki outputowe per user

### Język polski
- [ ] Przetestować generację wideo w języku polskim (temat PL → skrypt PL)
- [ ] Przetestować polskie głosy TTS (edge_tts: `pl-PL-MarekNeural`, `pl-PL-ZofiaNeural`)
- [ ] Sprawdzić jakość polskich napisów (UTF-8, znaki diakrytyczne)
- [ ] Dodać PL do listy języków w UI jeśli brakuje — patch oznaczony `# PATCHED`

---

## Stage 2 — Brand & Deploy
- [ ] Wybrać nazwę marki i domenę
- [ ] Wybrać hosting (VPS)
- [ ] Przygotować `infra/docker-compose.prod.yml` (poza katalogiem upstream)
- [ ] SSL + reverse proxy (Caddy lub Nginx)

## Stage 3 — SaaS overlay
- [ ] Landing page (`landing/`)
- [ ] System auth użytkowników (`saas/auth/`)
- [ ] Dashboard: historia jobów per user
- [ ] Kredyty / limity per plan
- [ ] Integracja Stripe
- [ ] Admin panel (statystyki, zarządzanie userami)

## Backlog / Pomysły
- Własny model TTS (bardziej naturalny głos)
- White-label (rebrand dla resellera)
- API publiczne dla integracji
- Obsługa wielu języków w UI
