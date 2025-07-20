# Cursor Rules


قوانین کرسر یا cursor rules, قانون هایی هستن که به جای اینکه هر سری توی پرامپتمون به کرسر بگیم, توی یه فایل .mdc مینویسیم و به کانتکستش اضافه میشه و توی جوابش رعایت میکنه اون قوانین رو.

### ۳ مدل rule داریم تو کرسر:
<div dir="rtl">
- Project rules
توی cursor/rules. ذخیره میشه 
<br>
- User Rules
اینا رول های گلوبال هستن و توی settings ذخیره میشن
<br>
- .cursorrules (legacy)
هنوز ساپورت میشه ولی deprecated شده.
</div>
<br>

## Project Rules
### آناتومی rule 

هر فایل rule با فرمت `.mdc` نوشته می‌شه، که شامل metadata هم میشه.

Metadata:

- `description`: توضیح متنی برای فهم مدل اینکه این rule چه موقع باید اعمال بشه
    
- `globs`: تعیین scope (مثلاً فقط فایل‌های خاص)
    
- `alwaysApply`: اگر `true` باشه، همیشه روی تمام فایل‌ها اعمال می‌شه

|Rule Type|Description|
|---|---|
|`Always`|Always included in model context|
|`Auto Attached`|Included when files matching a glob pattern are referenced|
|`Agent Requested`|Available to AI, which decides whether to include it. Must provide a description|
|`Manual`|Only included when explicitly mentioned using `@ruleName`|


مثال:

```
---
description: RPC Service boilerplate
globs: 
alwaysApply: false
---

- Use our internal RPC pattern when defining services
- Always use snake_case for service names.

@service-template.ts
```


### چطوری این rules اعمال می‌شن؟

دو مرحله داره:

1. **Inject**: اگر `alwaysApply: true` یا فایل داخل `globs` باشه، rule وارد context می‌شه.
    
2. **Activate**: مدل خودش تشخیص می‌ده که آیا rule مرتبطه یا خیر (بر اساس `description`)

ترکیب هوشمندانه `globs` + `description` باعث می‌شه که:
<div dir="rtl">
- مدل context کمتری مصرف کنه
<br>
- و فقط وقتی rule دیده بشه که مرتبط باشه
</div>
<br>

### نوشتن و سازماندهی قوانین پروژه (ٍٔNested Rules)
<div dir="rtl">
- همیشه rules رو داخل `.cursor/rules/` قرار بده تا versioned و scoped باشن
<br>
- قوانینی که مربوط به فولدر یا تکنولوژی خاص هستن، می‌تونی subfolder ایجاد کنی تا فقط روی اون بخش اعمال بشن
</div>
<br>

  مثال:

```
project/
  .cursor/rules/        # Project-wide rules
  backend/
    server/
      .cursor/rules/    # Backend-specific rules
  frontend/
    .cursor/rules/      # Frontend-specific rules
```
تعدادشون زیاد نشه (پیشنهاد: زیر ۵۰۰ خط کد)


### چطور rule رو دستی فراخوانی یا غیرفعال کنیم؟
<div dir="rtl">
- با نوشتن ``@ruleName`` داخل chat می‌تونید rule خاصی رو وارد context کنید
<br>
- یا از `/Generate Cursor Rules` استفاده کنید تا خود Agent rule بسازه
</div>
<br>

## User Rules
توی settings خود کرسر و قسمت Rules, میتونید تعریف کنید. مثلا:

```
Please reply in a concise style. Avoid unnecessary repetition or filler language.
```

**استفاده کردن از قوانین کرسر یکی از راه های منیج کردن کانتکست هست.**

---

*بخش ۱۱ ->[Cursor MCP](11-cursor-mcp.md)* 
