# tryb-przetrwania-site

Landing page do filmu sophie_dbc o trybie przetrwania. Zbiera maile na newsletter „Nauka Tygodnia" i wysyła PDF freebie przez Make.com.

Hostowanie: **GitHub → Vercel** (statyczna strona, zero buildowania).

---

## Struktura

```
tryb-przetrwania-site/
├── index.html          ← landing
├── cover.png           ← duża okładka PDF (do hero na stronie)
├── cover-email.png     ← mniejsza okładka (do maila z Make)
└── README.md           ← ten plik
```

---

## Jak postawić na Vercelu

### Wariant A — przez Vercel CLI (najszybsze)

```bash
cd tryb-przetrwania-site
npx vercel --prod
```

Zaloguj się przez GitHub, gdy pyta. Projekt nazwij **`tryb-przetrwania`** — wtedy URL będzie automatycznie `https://tryb-przetrwania.vercel.app` (ten sam, który już jest wpisany w mail w Make).

### Wariant B — przez UI Vercela

1. Wrzuć ten folder do repo na GitHubie (np. nowe repo `tryb-przetrwania-site`)
2. Wejdź na vercel.com → **Add new** → **Project**
3. Wybierz repo z GitHuba
4. **Project Name:** `tryb-przetrwania` (ważne — ten sam URL jest w mailu w Make)
5. **Framework Preset:** Other
6. **Build Command:** zostaw puste
7. **Output Directory:** zostaw puste (Vercel sam zobaczy `index.html`)
8. Deploy

URL będzie `https://tryb-przetrwania.vercel.app`.

---

## Co jest pod maską

- **Webhook Make:** `https://hook.eu1.make.com/2bomeyyqk0js3cgumu6dywsh8yi8tpba` (wspólny dla wszystkich freebie)
- **freebieId:** `tryb_przetrwania` (rozpoznawany przez gałąź routera w scenariuszu Make 5849603)
- **Cover image w mailu:** odsyła do `https://tryb-przetrwania.vercel.app/cover-email.png` — dlatego ważne, żeby projekt na Vercelu nazywał się dokładnie `tryb-przetrwania`

Jeśli musisz nazwać projekt inaczej (bo `tryb-przetrwania` zajęte): zmień URL w mailu w Make (edytuj moduł e-maila gałęzi „Freebie: tryb_przetrwania" — w polu Content znajdź `tryb-przetrwania.vercel.app` i podmień na swoją domenę).

---

## Co jeszcze musi zrobić Zosia (3 rzeczy, ~10 min)

1. **Wgraj `Wyjdz-z-trybu-przetrwania-FINAL.pdf` na Drive** (folder zz/) → udostępnij „każdy z linkiem" → wyciągnij ID pliku z linka (ciąg między `/d/` i `/view`)
2. **Otwórz [Make scenario](https://eu1.make.com/925322/scenarios/5849603/edit)** → kliknij moduł e-mail w gałęzi „Freebie: tryb_przetrwania" → w polu Content znajdź `PLACEHOLDER-PDF-ID` → podmień na ID z punktu 1 → zapisz
3. **Postaw stronę na Vercelu** (instrukcja wyżej)

Potem testuj na swoim drugim mailu i sprawdzaj Sheets + skrzynkę. ✦
