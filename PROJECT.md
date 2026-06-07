# MoneyPrinterTurbo — Plan projektu SaaS

## Czym jest projekt

Budujemy SaaS na bazie open-source [MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo) — narzędzia do automatycznego generowania wideo z tekstem, muzyką i napisami za pomocą LLM.

Podejście: minimalnie inwazyjna warstwa SaaS na gotowym silniku. Silnik żyje swoim życiem (możemy pullować upstream), a nasza warstwa (auth, billing, branding) dokładana jest obok/nad nim.

---

## Stage 1 — PoC lokalny (aktualny)

**Cel:** uruchomić aplikację lokalnie, przetestować możliwości silnika, poznać API i WebUI.

- [x] Sklonować repo z upstream
- [ ] Uruchomić lokalnie (Python/uv + config)
- [ ] Skonfigurować klucze API (LLM, TTS, wideo)
- [ ] Wygenerować pierwsze testowe wideo
- [ ] Zmapować punkty rozszerzeń pod SaaS

---

## Stage 2 — Brand, domena, serwer

Do ustalenia:
- nazwa marki / domena
- hosting (VPS, cloud — do wyboru przy deploymencie)
- stack deploymentu (Docker Compose, wstępnie wystarczy)

---

## Stage 3 — SaaS overlay

Funkcjonalności do dodania **bez modyfikowania silnika**:

1. **Landing page** — statyczna strona marketingowa (osobne repo lub `/landing`)
2. **Auth użytkowników** — logowanie/rejestracja, JWT/session (np. Supabase Auth lub własne)
3. **Dashboard użytkownika** — historia wideo, ustawienia, kredyty
4. **Płatności** — Stripe (lub Paddle), plany subskrypcyjne / pay-per-video
5. **Multi-tenancy** — izolacja zasobów per user (kolejka zadań, limity)
6. **API Gateway** — proxy między frontem SaaS a silnikiem MoneyPrinterTurbo

---

## Zasady pracy z upstream

```bash
# Pobierz aktualizacje z oryginału
git fetch upstream
git merge upstream/main

# Własne zmiany trzymamy na feature branches
git checkout -b feature/saas-auth
```

Własny kod SaaS trzymamy w katalogach nieprzekrywających się z upstream:
- `saas/` — auth, billing, dashboard
- `landing/` — strona marketingowa
- `infra/` — docker-compose produkcyjny, nginx, certbot

Pliki upstream edytujemy tylko gdy nie ma innego wyjścia — wtedy oznaczamy `# PATCHED` z komentarzem dlaczego.

---

## Tech stack (wstępny)

| Warstwa | Technologia |
|---------|-------------|
| Silnik wideo | MoneyPrinterTurbo (Python/FastAPI) |
| SaaS backend | FastAPI lub Next.js API routes |
| SaaS frontend | Next.js + Tailwind |
| Auth | Supabase Auth lub Clerk |
| Płatności | Stripe |
| DB | PostgreSQL (Supabase lub własny) |
| Deploy | Docker Compose + Caddy/Nginx |
| LLM | Claude (Anthropic API) |
