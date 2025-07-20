# Prompt Engineer

پرامپت نوشتن هم هنره هم علم.
یه پرامپت خوب ظرافت داره و هدفمنده.

**یه پرامپت خوب:**
<div dir="rtl">
- انقد کامل و واضحه که جایی برای حدس زدن برای LLM نمیزاره
<br>
- ساختار داره -> مثل یه دستورالعمله
<br>
- از کلمات ساده و مستقیم و جملات کوتاه استفاده میکنه
</div>
<br>
یادتون باشه: 

**Garbage in = Garbage out**

### فرمول پرامپت نویسی
<div dir="rtl">
- Role (نقش)
<br>
- Goal (هدف)
<br>
- Instructions (دستورالعمل)
<br>
- Examples (مثال ها)
<br>
- Format (شکل)
</div>
<br>

### نقش یا Role :

در راستای تسک هایی که از AI میخواین بهش بگید که تخصصش چیه. مثال:

```
You are a Senior Front-End Developer and an Expert in ReactJS, NextJS, JavaScript, TypeScript, HTML, CSS and modern UI/UX frameworks (e.g., TailwindCSS, Shadcn, Radix). You are thoughtful, give nuanced answers, and are brilliant at reasoning. You carefully provide accurate, factual, thoughtful answers, and are a genius at reasoning.
```

### هدف یا Goal :

مشخصا باید بهش توضیح بدید چی میخواین. هرچی دقیق تر بهتر!

مثال:
```
I want to lazy-load podcast player components that are currently blocking my LCP score.
```


### دستورالعمل یا Instruction :

دستورالعمل باعث میشه ai خودش حدس نزنه چیکار کنه. کلا هرجا داشت حدس میزد بدونید یه جای راه رو دارید اشتباه میرید.

مثال:
```
Avoid using third-party libraries unless absolutely necessary.
Write clear comments for every block of logic.
```


### مثال ها یا Examples :

خیلی مهمه چون ai فقط با پترن ها سر و کار داره و باید پترن کدنویسی شما رو هم بدونه که بتونه شبیه اون بزنه.
مثال:
```js
Follow this pattern:
const LazyPlayer = dynamic(() => import('./Player'), { ssr: false });
```

### شکل یا Format :

این برای خروجیه که مشخص میکنید چه فرمتی داشته باشه.
مثال:
```
Return only the refactored code in a single JavaScript block. No explanation.
```


در نهایت, همه رو با هم بهش میدید:
```
I want to refactor a component that mixes data-fetching and UI logic into a clean separation of concerns.

Avoid adding new libraries.
Use custom hooks.
Comment key sections.

Follow this pattern:
const LazyPlayer = dynamic(() => import('./Player'), { ssr: false });

Return only the new component and the new hook in a single code block.
```
‍‍‍

### یه فریم ورک دیگه از Google Prompting Course

توی کورس prompting گوگل, فریم ورک استفاده از AI رو اینجوری گفته:
- Task
- Context
- references
- evaluate
- iterate


**این شکلیه:**

تسک تعریف میکنیم براش ([تسک بندی](05-breaking-down.md))

کانتکست درست و کامل رو میدیم بهش (تو قسمت [context engineering](08-context-engineering.md) راجع بهش گفتیم),

رفرنس ها همون مثال هاست که بالاتر گفتم,

حالا بعد از اینکه جواب رو گرفتیم از LLM, اونو کامل بررسی میکنیم (evaluate)

اگر جوابی که میخواستیم نیست -> یه قدم به عقب برمیگردیم و اصطلاحا iterate میکنیم.

### 🌀 Iterative Prompting

پرامپت نوشتن یه مهارته و نیاز به تمرین داره. 
با سعی و خطا در نهایت متوجه میشی چی کار میکنه و چی کار نمیکنه.

تو این مرحله باید بهش فیدبک بدیم و بگیم چی کار نمیکنه و چی داره کار میکنه و ازش بخوایم دوباره اون قسمتی که کار نمیکنه رو فیکس کنه با یه روش دیگه.

به این فرایند می‌گن: **iterative prompting**  

### نکته های پیشرفته تر

### Prompt Chaining (زنجیره‌سازی پرامپت‌ها)

بعضی وقتا نمیشه همه‌ی چیزی که می‌خواین رو تو یه پرامپت بگین. یا حتی نباید بگین. چون هم باعث overload تو context می‌شه، هم مدل گیج می‌شه.  
در واقع جواب‌هایی که از پرامپت اول می‌گیرین، می‌شن ورودی پرامپت بعدی.

**مثال:**
<div dir="rtl">
1. «لیستی از تمام مشکلات performance توی این کد بده»
<br>
2. «حالا به ترتیب اولویت بگو کدوماش ارزش وقت گذاشتن دارن»
<br> 
3. «اولی رو بهینه کن و فقط کد نهایی رو بده»
</div>
<br>
 به جای اینکه یهویی بگی "کلش رو درست کن" داری قدم به قدم مدل رو جلو می‌بری. 

### Chain of Thought Prompting (تفکر زنجیره‌ای)

به جای اینکه از مدل فقط جواب نهایی رو بخوای، ازش بخواه قبلش فکر کنه، تحلیل کنه، قدم‌به‌قدم استدلال بیاره و بعد نتیجه بده.

**چرا مهمه؟**  
چون LLMها وقتی مجبور می‌شن reasoning کنن، احتمال اینکه جواب درست بدن خیلی بیشتر می‌شه. مخصوصاً وقتی جواب به context، logic یا چند مرحله فکر نیاز داره.

**مثال:**
```
Let's think step by step. First, explain the logic behind how you'd lazy load this component without affecting SEO. Then, suggest the implementation.
```


**یا برای دیباگ کردن:**
```
Before writing the fix, analyze the root cause of the error and explain your reasoning. Then implement the fix.
```


این روش نه فقط برای گرفتن جواب بهتره، بلکه باعث می‌شه خودت هم روند حل مسئله رو بهتر بفهمی و از مدل یاد بگیری. (همچنین یک جور safety net هم هست: اگه reasoning اشتباه بود، می‌تونی قبل از اجرای کد جلوش رو بگیری.)

### Meta Prompting

**چی هست؟**  
از مدل بخوای خودش یه پرامپت بهتر برای تسک بسازه!

**مثال:**
```
What would be the best way to ask you to implement this feature cleanly and efficiently?
```


###  پرامپت‌هات رو ذخیره کن (Personal Prompt Library)

**یه کتابخونه شخصی از پرامپت‌ها** درست کن:

- 🧱 **Feature Prompts:** برای ساختن فیچر جدید
    
- 🛠 **Fix Prompts:** برای دیباگ و رفع باگ
    
- 🧹 **Refactor Prompts:** برای تمیز کردن یا بهبود کد
    
- 🧪 **Test Prompts:** برای تولید تست یونیت
    
- 🧠 **Architecture Prompts:** برای مشورت در مورد ساختار پروژه


---

*بخش ۱۰ ->[قوانین کرسر](10-cursor-rules.md)* 
