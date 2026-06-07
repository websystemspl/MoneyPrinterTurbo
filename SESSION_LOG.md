# Session Log

## Sesja 1 — 2026-06-07 (PoC lokalny)

### Co zrobiono
1. Sklonowano repo `harry0703/MoneyPrinterTurbo` do `Nextcloud/Prace bieżące/MoneyPrinterTurbo/`
2. Remote `origin` → `https://github.com/websystemspl/MoneyPrinterTurbo.git` (org websystemspl)
3. Remote `upstream` → `https://github.com/harry0703/MoneyPrinterTurbo.git` (źródło do aktualizacji)
4. Zainstalowano `uv`, wykonano `uv sync` — środowisko Python w `.venv`
5. Skopiowano `config.toml`, wpisano klucze: Pexels API + OpenAI API (GPT-4o-mini)
6. **Patch upstream:** `webui.sh` linia 59 — dodano cudzysłów wokół `$PORT_CHECK_CMD` (ścieżka ze spacją powodowała split). Oznaczono `# PATCHED`.
7. Uruchomiono WebUI na `http://127.0.0.1:8501`
8. Wygenerowano pierwsze wideo: ~148 sekund, 52 klipy Pexels 1080x1920, TTS edge_tts, skrypt GPT-4o-mini

### Obserwacje z pierwszego testu
- Silnik działa poprawnie end-to-end
- Jakość "kiepska ale działa" — do dostrojenia: prompty LLM, dobór klipów, głos TTS
- Jeden warning MoviePy (0 bytes at frame 360) — niekrytyczny, ffmpeg sobie radzi
- Czas generacji: ~13 min dla ~150s wideo (głównie ffmpeg concat)
- Font domyślny: `MicrosoftYaHeiBold.ttc` — trzeba sprawdzić jak radzi sobie z PL

### Pliki dodane przez nas (poza upstream)
- `PROJECT.md` — plan 3-stagowy SaaS
- `TODO.md` — lista zadań per stage
- `SESSION_LOG.md` — ten plik
- `credentials.md` — klucze API (w `.gitignore`, nie commitowane)
- `config.toml` — konfiguracja lokalna (w `.gitignore`)

### Zasada pracy (WAŻNE dla kolejnych sesji)
**Własny kod ZAWSZE w osobnych katalogach:** `saas/`, `landing/`, `infra/`, `patches/`
Pliki upstream edytujemy tylko gdy nie ma wyjścia — oznaczamy `# PATCHED` z powodem.
Aktualizacja silnika: `git fetch upstream && git merge upstream/main`, re-aplikuj patche z `patches/`.

### Co dalej (Stage 1 cont. / Stage 2)
1. Przetestować język polski — głosy `pl-PL-MarekNeural`, `pl-PL-ZofiaNeural`
2. Zmapować API silnika (`/app/routers/`) pod kątem integracji SaaS
3. Podjąć decyzję: brand + domena + serwer (Stage 2)
4. Przygotować `infra/docker-compose.prod.yml` pod deploy

### Uruchomienie lokalne
```bash
cd "Nextcloud/Prace bieżące/MoneyPrinterTurbo"
PATH="$HOME/.local/bin:$PATH" ./webui.sh
# → http://127.0.0.1:8501
```
