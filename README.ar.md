<h1 align="center" dir="rtl">AMUX</h1>
<h3 align="center" dir="rtl">أول محطة طرفية بتسريع GPU تدعم العربية</h3>

<p align="center">
  <a href="https://github.com/AICCodingCo/AMUX/releases/latest/download/AMUX-macos.dmg">
    <img src="./docs/assets/macos-badge.png" alt="تحميل AMUX لنظام macOS" width="180" />
  </a>
</p>

<p align="center">
  العربية | <a href="README.md">English</a>
</p>

<div dir="rtl">

## ما هو AMUX؟

AMUX (Arabic MUX) هو نسخة معدّلة من [cmux](https://github.com/manaflow-ai/cmux) تضيف دعم عرض النص العربي واللغات ذات الاتجاه من اليمين لليسار (RTL) في المحطة الطرفية. حالياً، النص العربي يظهر بأحرف مفصولة ومعكوسة في كل محطات طرفية GPU المتسارعة — Ghostty وcmux وKitty وAlacritty. AMUX يحل هذه المشكلة.

تم بناؤه بواسطة [AICC (شركة الذكاء الاصطناعي بالقاهرة)](https://github.com/AICCodingCo) كجزء من مهمة أوسع: **بناء بنية تحتية للذكاء الاصطناعي للواقع غير اللاتيني.** إذا كانت أدوات البرمجة بالذكاء الاصطناعي تعمل في المحطات الطرفية، والمحطات الطرفية لا تستطيع عرض العربية، فإن أكثر من ٤٠٠ مليون ناطق بالعربية مستبعدون من ثورة البرمجة بالذكاء الاصطناعي.

## المميزات

كل مميزات cmux، بالإضافة إلى:

- **تشكيل النص العربي** — الحروف تتصل بالأشكال السياقية الصحيحة (أول، وسط، آخر، منفصل)
- **العرض ثنائي الاتجاه** — النص العربي/العبري يُعرض بالترتيب البصري الصحيح من اليمين لليسار باستخدام خوارزمية يونيكود ثنائية الاتجاه (UAX #9)
- **دعم التشكيل** — علامات التشكيل (فتحة، كسرة، ضمة، شدة، إلخ) توضع بشكل صحيح
- **النص المختلط** — العربية والإنجليزية في نفس السطر يُعرضان بشكل صحيح
- **دعم العبرية** — عرض RTL يعمل للنص العبري أيضاً

## التثبيت

### التحميل

حمّل أحدث ملف `.dmg` من [الإصدارات](https://github.com/AICCodingCo/AMUX/releases).

### البناء من المصدر

المتطلبات: macOS، Zig 0.15.2+، Xcode

```bash
git clone https://github.com/AICCodingCo/AMUX.git
cd AMUX
git submodule update --init --recursive
./scripts/setup.sh
./scripts/reload.sh --tag arabic
```

## جرّبه

```bash
echo "عربي: مرحبا بالعالم"
echo "مختلط: Hello مرحبا World"
echo "تشكيل: بِسْمِ اللَّهِ الرَّحْمَنِ الرَّحِيمِ"
```

## شكر وتقدير

AMUX مبني على أعمال مفتوحة المصدر ممتازة:

- **[cmux](https://github.com/manaflow-ai/cmux)** بواسطة Manaflow AI — المحطة الطرفية التي بنينا عليها (AGPL-3.0)
- **[Ghostty](https://github.com/ghostty-org/ghostty)** بواسطة Mitchell Hashimoto — محرك المحطة الطرفية المتسارع بـ GPU (MIT)
- **[itijah](https://github.com/DiaaEddin/itijah)** بواسطة [@DiaaEddin](https://github.com/DiaaEddin) — مكتبة Zig خالصة لخوارزمية يونيكود ثنائية الاتجاه (MIT)
- **[ghostty PR #11079](https://github.com/ghostty-org/ghostty/pull/11079)** — تنفيذ RTL الذي دمجناه
- **[commandlinetips/ghostty](https://github.com/commandlinetips/ghostty)** — نسخة تجريبية سابقة لدعم RTL في Ghostty باستخدام FriBidi

## الترخيص

AMUX مرخص تحت **رخصة GNU Affero العمومية الإصدار 3.0 أو أحدث** (AGPL-3.0-or-later)، موروثة من cmux.

---

<p align="center">
  بناء <a href="https://github.com/AICCodingCo">AICC</a> — بناء بنية تحتية للذكاء الاصطناعي للواقع غير اللاتيني
</p>

</div>
