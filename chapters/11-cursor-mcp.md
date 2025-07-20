# Cursor MCP

###  MCP (Model Context Protocol) چیه؟

وMCP یه پروتکل باز هست (شبیه به USB برای AI) که به Cursor اجازه می‌ده به ابزارها و منابع خارجی وصل بشه: بانک‌داده‌ها، مستندات، سیستم‌های داخلی، GitHub، Figma و حتی تست‌ها و مانیتورینگ. این یعنی دیگه لازم نیست همیشه context رو با copy/paste بهش بدی, خودش مستقیم به سیستم‌ها دسترسی داره.


###  چرا MCP برای برنامه نویس ها مفیده؟
<div dir="rtl">
- عمق context بدون زحمت:
<br>
    کرسر می‌تونه مستندات Notion یا Google Drive یا DB رو بخونه. 
<br>
- ابزار یکپارچه:  
<br>
    می‌تونید Cursor رو وصل کنید به GitHub، Figma, Chrome browser، Sentry یا Postgres و مستقیم توی ادیتور براش دستورات بدید.
</div>


###  چطوری MCP رو فعال و استفاده کنیم؟
<div dir="rtl">
۱. اضافه کردن server ها رو: 
<br>
    از توی `Cursor Settings → Features → MCP` می‌تونین MCP server اضافه کنید 
<br>
۲. فایل کانفیگ MCP: 
<br>
    توی پروژه‌تون `.cursor/mcp.json` بسازید، یا global config داشته باشید. بعد برای هر سرور، `command`, `args`, `env` تنظیم کنین.
<br>
۳. فعال‌سازی در chat: 
<br>
    وقتی یه ابزار MCP در دسترس باشه، Composer Agent اون رو نشون می‌ده و برای استفاده، ازتون اجازه می‌پرسه.
</div>
<br>

###  مثال عملی با MCP

برای خوندن مستندات از notion:
<div dir="rtl">
۱. Notion MCP server نصب می‌کنی و add to cursor
<br>
۲. توی چت prompt می‌دی:
 “Using Notion MCP, fetch the API spec page under 'Project Spec'”
<br>
۳. Cursor خودش درخواست MCP server رو می‌فرسته، مدل مستندات رو می‌خونه، و پاسخ می‌ده.
</div>

این یعنی دیگه نیازی نیست فایل‌ها رو دستی وارد کنی.

 یا مثلا میتونی از MCP فیگما استفاده کنی و توی چت کرسر بنویسی که ui رو از فیگما ببینه و کدش رو پیاده سازی کنه.

---

*بخش ۱۲ ->[امنیت](12-security.md)* 
