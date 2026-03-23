<h1 align="center" dir="rtl">amux</h1>
<h3 align="center" dir="rtl">محطة طرفية بتسريع GPU تدعم العربية</h3>

<p align="center">
  <a href="https://github.com/alymoursy/amux/releases/latest/download/amux-macos.dmg">
    <img src="./docs/assets/macos-badge.png" alt="تحميل amux لنظام macOS" width="180" />
  </a>
</p>

<p align="center">
  العربية | <a href="README.md">English</a>
</p>

<div dir="rtl">

### قبل وبعد

| قبل (cmux) | بعد (amux) |
|---|---|
| <img src="./docs/assets/before-cmux-arabic.png" alt="قبل: حروف مفصولة في cmux" width="450" /> | <img src="./docs/assets/after-amux-arabic.png" alt="بعد: حروف متصلة في amux" width="450" /> |
| حروف مفصولة ومعكوسة | حروف متصلة بالشكل الصحيح مع عرض ثنائي الاتجاه |

## ما هو amux؟

amux (Arabic MUX) هو نسخة معدّلة من [cmux](https://github.com/manaflow-ai/cmux) تضيف دعم عرض النص العربي واللغات ذات الاتجاه من اليمين لليسار (RTL) في المحطة الطرفية. حالياً، النص العربي يظهر بأحرف مفصولة ومعكوسة في كل محطات طرفية GPU المتسارعة — Ghostty وcmux وKitty وAlacritty. amux يحل هذه المشكلة.

تم بناؤه بواسطة [شركة كايرو للذكاء الاصطناعي](https://artificialintelligencecc.com). بناء ذكاء اصطناعي للواقع العربي. إذا كانت أدوات البرمجة بالذكاء الاصطناعي تعمل في المحطات الطرفية، والمحطات الطرفية لا تستطيع عرض العربية، فإن أكثر من ٤٠٠ مليون ناطق بالعربية مستبعدون من ثورة البرمجة بالذكاء الاصطناعي.

## المميزات

كل مميزات cmux، بالإضافة إلى:

- **تشكيل النص العربي** — الحروف تتصل بالأشكال السياقية الصحيحة (أول، وسط، آخر، منفصل)
- **العرض ثنائي الاتجاه** — النص العربي يُعرض بالترتيب البصري الصحيح من اليمين لليسار باستخدام خوارزمية يونيكود ثنائية الاتجاه (UAX #9)
- **دعم التشكيل** — علامات التشكيل (فتحة، كسرة، ضمة، شدة، إلخ) توضع بشكل صحيح
- **النص المختلط** — العربية والإنجليزية في نفس السطر يُعرضان بشكل صحيح
- **كل مميزات cmux** — تبويبات عمودية، أجزاء مقسمة، إشعارات وكلاء الذكاء الاصطناعي، متصفح مدمج، توافق مع إعدادات Ghostty

## التثبيت

### التحميل

حمّل أحدث ملف `.dmg` من [الإصدارات](https://github.com/alymoursy/amux/releases).

> **macOS Gatekeeper:** التطبيق غير موثق بعد (بانتظار موافقة حساب مطور Apple). إذا قال macOS أنه "لا يمكن فتحه" أو أراد نقله للسلة:
> 1. اذهب إلى **إعدادات النظام > الخصوصية والأمان**
> 2. مرر لأسفل — سترى رسالة عن حظر amux
> 3. اضغط **فتح على أي حال**
>
> أو من Terminal:
> ```
> xattr -cr /Applications/amux.app
> open /Applications/amux.app
> ```
> سيتم حل هذا بمجرد توثيق التطبيق.

### البناء من المصدر

المتطلبات: macOS، Zig 0.15.2+، Xcode

```bash
git clone https://github.com/alymoursy/amux.git
cd amux
git submodule update --init --recursive
./scripts/setup.sh
./scripts/reload.sh --tag arabic
```

## كيف يعمل

عرض RTL مدعوم بواسطة [itijah](https://github.com/DiaaEddin/itijah)، مكتبة Zig خالصة لخوارزمية يونيكود ثنائية الاتجاه (UAX #9). تم تطوير التكامل في [ghostty PR #11079](https://github.com/ghostty-org/ghostty/pull/11079) بواسطة [@DiaaEddin](https://github.com/DiaaEddin)، والذي دمجناه في وحدة Ghostty الفرعية.

## جرّبه

```bash
echo "عربي: مرحبا بالعالم"
echo "مختلط: Hello مرحبا World"
echo "تشكيل: بِسْمِ اللَّهِ الرَّحْمَنِ الرَّحِيمِ"
```

## القيود المعروفة

- **موضع المؤشر** — حركة المؤشر خاطئة عند كتابة RTL في shell تفاعلي. المخرجات الجاهزة (`echo`، `cat`) تُعرض بشكل صحيح.
- **التحديد** — تحديد النص يتبع الترتيب المنطقي، ليس الترتيب البصري.
- **التفاف سطور RTL** — الأسطر العربية الطويلة تلتف باستخدام التفاف LTR القياسي.

## شكر وتقدير

amux مبني على أعمال مفتوحة المصدر ممتازة:

### التبعيات الأساسية

- **[cmux](https://github.com/manaflow-ai/cmux)** بواسطة Manaflow AI — المحطة الطرفية التي بنينا عليها. amux يرث كل مميزات cmux. مرخص تحت AGPL-3.0-or-later.
- **[Ghostty](https://github.com/ghostty-org/ghostty)** بواسطة Mitchell Hashimoto — محرك المحطة الطرفية المتسارع بـ GPU. مرخص تحت MIT.
- **[itijah](https://github.com/DiaaEddin/itijah)** بواسطة [@DiaaEddin](https://github.com/DiaaEddin) — مكتبة Zig خالصة لخوارزمية يونيكود ثنائية الاتجاه. مرخص تحت MIT.

### تنفيذ RTL

عرض العربية/RTL في amux مبني على **[ghostty PR #11079](https://github.com/ghostty-org/ghostty/pull/11079)** بواسطة [@DiaaEddin](https://github.com/DiaaEddin)، والذي يضيف تشكيل نص ثنائي الاتجاه لمحرك الخطوط في Ghostty. دمجنا هذا الـ PR في وحدة Ghostty الفرعية.

### إلهام

- **[commandlinetips/ghostty](https://github.com/commandlinetips/ghostty)** — نسخة تجريبية سابقة لدعم RTL في Ghostty باستخدام FriBidi
- **[cmux issue #547](https://github.com/manaflow-ai/cmux/issues/547)** — طلب ميزة RTL في cmux
- **[ghostty issue #1442](https://github.com/ghostty-org/ghostty/issues/1442)** — مشكلة RTL في Ghostty الأصلي

## الترخيص

amux مرخص تحت **رخصة GNU Affero العمومية الإصدار 3.0 أو أحدث** (AGPL-3.0-or-later)، موروثة من cmux.

انظر [LICENSE](LICENSE) للنص الكامل. تراخيص الطرف الثالث مدرجة في [THIRD_PARTY_LICENSES.md](THIRD_PARTY_LICENSES.md).

---

<p align="center">
  بناء <a href="https://artificialintelligencecc.com">شركة كايرو للذكاء الاصطناعي</a> — بناء ذكاء اصطناعي للواقع العربي
</p>

</div>
