# امنیت



**این بخش رو فرانت اند کار هایی که میخوان کد بکند با ai بزنن جدی بگیرن مخصوصا**
### امنیت کد موقع استفاده از AI

وقتی از یه AI کمک می‌گیرید که کد رو بنویسه یا یه فیچر رو پیاده کنه، همیشه این سؤال باید تو ذهنت باشه:

> «آیا این کدی که AI زده، امنه؟ یا فقط کار می‌کنه؟»

واقعیت اینه که **AI دنبال امنیت نیست، دنبال حل تسکه.** و اگه ازش نخواین که به امنیت فکر کنه، احتمال زیاد یه سوراخ بزرگ توی اپلیکیشنتون جا می‌ذاره.

### خطرهای رایج در کدی که AI تولید می‌کنه:
<div dir="rtl">
- استفاده از توکن یا API Key به‌صورت مستقیم تو کد
<br>
- نداشتن input validation و در معرض بودن به حملات XSS یا SQL Injection
<br>
- نداشتن authentication/authorization درست برای route ها
<br>
- ذخیره کردن رمز عبور و دیتای حساس بدون هش کردن
<br>
- ساختن endpointهایی که هر کسی می‌تونه صداشون بزنه
<br>
- Rate Limiting
<br>
- Row Level Security (RLS)
<br>
- Spam Protection
<br>
</div>

### چطور امنیت رو توی فرآیند کدنویسی AI-محور وارد کنیم؟

#### - امنیت رو توی پرامپت بیار

موقع پرامپت دادن، دقیقاً بگید امنیت هم مهمه. مثلاً:


```
Build a login endpoint in Express, but make sure to validate inputs, hash passwords using bcrypt, and avoid common security issues.
```

یا حتی مستقیم‌تر:
```
Make sure this endpoint is protected against SQL injection and does not expose sensitive data.

```

```
Review this code and improve its security. What vulnerabilities do you see?
```


#### - خودتون هم امنیت یاد بگیرین

هوش مصنوعی نمی‌تونه چیزی رو که **خودتون نمی‌فهمید** بهتون یاد بده. اگه ندونید که CSRF چیه، حتی اگه تو کد باشه نمی‌تونید پیدا کنید. پس سرچ کنید، پایه‌ های امنیت وب یا بک‌اند رو بشناسید. این باعث می‌شه بتونید به AI هم بهتر بگید چی می‌خواین.

### - Rate Limiting: خط ترمزی برای سوءاستفاده‌ها

وRate Limiting یکی از ساده‌ترین ولی مهم‌ترین روش‌های دفاعی برای محافظت از API یا سروره. مخصوصاً وقتی از AI می‌خواین یه endpoint بسازه، معمولاً این موضوع رو نادیده می‌گیره. اگه route مثل `/login` یا `/feedback` یا حتی `/api/send-email` دارید، باید یه مکانیزم Rate Limiting بذارید تا کسی نتونه صد بار تو ثانیه ریکوئست بفرسته. اگه نذارید، ممکنه هدف حملات brute-force، spam یا DDoS بشید. مثلاً توی Node با پکیجی مثل `express-rate-limit` می‌تونید بگید هر IP فقط ۵ درخواست در دقیقه بدید. وقتی با AI دارید کد می‌زنید، توی پرامپت حتماً اضافه کنید:  
‍
```
Add basic rate limiting to prevent abuse.
```

### Row-Level Security: دسترسی داده به سبک حرفه‌ای

اگه قراره دیتابیس‌ اطلاعات کاربران مختلف رو نگه داره، نباید همه چیز برای همه کاربرها قابل دسترسی باشه. Row-Level Security دقیقاً این‌جاست که وارد میشه. مثلاً فرض کن یه جدول داری به اسم `posts` و هر کاربر فقط باید بتونه پست‌های خودش رو ببینه. بدون RLS ممکنه یکی با یه کوئری ساده مثل `SELECT * FROM posts` کل دیتای همه کاربرها رو ببینه — فاجعه امنیتی!
وقتی دارید از یه AI coding agent مثل Cursor می‌خواین backend بنویسه، حتماً بگید:

> **"Enable row-level security on sensitive tables like 'users' or 'posts', and create policies to restrict access based on user_id."**

### محافظت در برابر اسپم: راه نجات فرم‌هات از بات‌ها

وقتی یه پروژه لانچ می‌کنید، مخصوصاً اگه فرم ثبت‌نام، لاگین، یا فرم تماس داری، باید همیشه به اسپمرها فکر کنید.

**چند راه مؤثر برای محافظت در برابر اسپم:**

#### 1. Rate Limiting

همون‌طور که قبلاً گفتیم، نذارید یه آی‌پی بتونه صد بار توی یه دقیقه فرم پر کنه.

#### 2. Honeypot Field

یه فیلد مخفی داخل فرم بذار (مثلاً با CSS `display: none`) و اگر پر شد → میفهمید که یه بات فرم رو پر کرده.

#### 3. reCAPTCHA یا hCaptcha

راه کلاسیک ولی همچنان مؤثر. Google reCAPTCHA یا hCaptcha جلوی خیلی از بات‌ها رو می‌گیره.

#### 4. Email verification

برای فرم‌های حساس مثل ثبت‌نام یا فیدبک، از کاربر بخواین با ایمیل تأیید کنه.

#### 5. Backend Validation

فقط سمت فرانت چک نکنید. حتماً سمت سرور دوباره بررسی کنید که فرم منطقی و معتبر باشه.

و وقتی دارید از AI coding agent مثل Cursor کمک می‌گیرید برای ساختن یه فرم یا endpoint، توی پرامپت بنویسین:

> **"Add basic spam protection like rate limiting, honeypot field, and server-side validation to this feedback endpoint."**

### پرامپت‌های خوب امنیتی برای چک کردن

- `Is this code vulnerable to XSS?`
    
- `Add input sanitization and validation.`
    
- `Ensure secure headers are set in Express.`
    
- `Does this React form expose any security risks?`
    
- `How can I make this upload feature more secure?`

### Security checklist

### Frontend Security

| | Security Measure | Description |
|---|-----------------|-------------|
| ☐ | Use HTTPS everywhere | Prevents basic eavesdropping and man-in-the-middle attacks |
| ☐ | Input validation and sanitization | Prevents XSS attacks by validating all user inputs |
| ☐ | Don't store sensitive data in the browser | No secrets in localStorage or client-side code |
| ☐ | CSRF protection | Implement anti-CSRF tokens for forms and state-changing requests |
| ☐ | Never expose API keys in frontend | API credentials should always remain server-side |

### Backend Security

| | Security Measure | Description |
|---|-----------------|-------------|
| ☐ | Authentication fundamentals | Use established libraries, proper password storage (hashing+salting) |
| ☐ | Authorization checks | Always verify permissions before performing actions |
| ☐ | API endpoint protection | Implement proper authentication for every API endpoint |
| ☐ | SQL injection prevention | Use parameterized queries or ORMs, never raw SQL with user input |
| ☐ | Basic security headers | Implement X-Frame-Options, X-Content-Type-Options, and HSTS |
| ☐ | DDoS protection | Use a CDN or cloud service with built-in DDoS mitigation capabilities |

### Practical Security Habits

| | Security Measure | Description |
|---|-----------------|-------------|
| ☐ | Keep dependencies updated | Most vulnerabilities come from outdated libraries |
| ☐ | Proper error handling | Don't expose sensitive details in error messages |
| ☐ | Secure cookies | Set HttpOnly, Secure and SameSite attributes |
| ☐ | File upload security | Validate file types, sizes, and scan for malicious content |
| ☐ | Rate limiting | Implement on all API endpoints, especially authentication-related ones |



پیشنهاد میکنم این چک لیست ها رو به global rule کرسرتون اضافه کنید.([Cursor Rules](10-cursor-rules.md))

---

*بخش ۱۳ ->[نکات تکمیلی](13-additional-tips.md)* 
