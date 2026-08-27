# TesterBot — tanıtım saytı (GitHub + Vercel)

Bu qovluq TesterBot məhsulunun tanıtım saytıdır — hazır, deploy üçün gözləyir.
Statik saytdır (build lazım deyil), Vercel-də bir neçə klikə canlıya çıxır.

```
testerbot-web/
├── index.html      ← saytın özü (hər şey içindədir)
├── testerbot.zip   ← "Pulsuz endir" düyməsinin verdiyi fayl (v2.1 alət)
├── favicon.svg     ← sayt ikonu
├── vercel.json     ← Vercel ayarları
└── README.md       ← bu fayl
```

---

## Ən asan yol — terminal yox (GitHub saytı + Vercel)

### 1. GitHub-da repo yarat
1. [github.com](https://github.com) → giriş et (hesabın yoxdursa pulsuz aç).
2. Sağ yuxarı **+** → **New repository**.
3. Ad ver: `testerbot-web` → **Public** → **Create repository**.

### 2. Faylları yüklə
1. Yeni repo səhifəsində **uploading an existing file** linkinə bas.
2. Bu qovluqdakı **bütün faylları** (index.html, testerbot.zip, favicon.svg, vercel.json) sürüşdürüb burax.
3. Aşağıda **Commit changes** düyməsinə bas.

### 3. Vercel-ə bağla
1. [vercel.com](https://vercel.com) → **Continue with GitHub** ilə giriş et.
2. **Add New… → Project**.
3. `testerbot-web` reposunu tap → **Import**.
4. Heç nəyi dəyişmə (Framework: **Other**, build lazım deyil) → **Deploy**.
5. ~30 saniyəyə saytın canlıdır: `testerbot-web.vercel.app` kimi bir ünvan verəcək.

Bitdi. Bundan sonra GitHub-a hər dəyişiklik yükləyəndə Vercel avtomatik yeniləyir.

---

## Terminal ilə (developer yolu)

```bash
cd testerbot-web
git init && git add . && git commit -m "TesterBot landing"
# GitHub-da boş repo yarat, sonra:
git remote add origin https://github.com/İSTİFADƏÇİ/testerbot-web.git
git branch -M main && git push -u origin main
```

Sonra Vercel-də reponu **Import** et, ya da Vercel CLI ilə:

```bash
npm i -g vercel
vercel        # ilk dəfə: layihəni bağla
vercel --prod # canlıya çıxar
```

---

## Öz domenini bağlamaq (istəyə bağlı)

Vercel → layihə → **Settings → Domains** → domenini yaz (məs. `testerbot.az`)
və göstərilən DNS qeydini domen provayderində əlavə et.

---

## Nə dəyişdirə bilərsən

- **Mətnlər / başlıqlar:** `index.html` içində birbaşa redaktə et.
- **Endirilən fayl:** `testerbot.zip`-i yeni versiya ilə əvəz et (adı eyni qalsın).
- **Rənglər:** `index.html`-in yuxarısındakı `:root { --accent … }` dəyişənləri.

---

## Növbəti mərhələ — işlək veb-tətbiq

Bu sayt **statikdir** (yalnız məhsulu göstərir). İstifadəçinin brauzerdə linki yazıb
canlı test işlətdiyi **işlək versiya** üçün crawler (Playwright) bir serverdə işləməlidir —
bu, Vercel-də mümkün deyil (serverless funksiyalar üçün çox ağır). O mərhələdə:

- **Frontend** → Vercel (bu repo böyüyür)
- **Crawler backend** → ayrı bir kiçik server (Railway / Render / Fly / Hetzner)

Hazır olanda birlikdə qurarıq.
