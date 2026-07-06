# جامپ‌لندر — راهنمای آموزشی استفاده از دستیار کدنویسی و جریان‌های AI-Assisted Development

---

## هدف این راهنما

هدف این راهنما این است که نشان دهد JumpLander چگونه می‌تواند به توسعه‌دهندگان کمک کند تا با کمک هوش مصنوعی:

- کد را بهتر بفهمند
- خطاها را دقیق‌تر بررسی کنند
- کد را مرحله‌به‌مرحله بهبود دهند
- از refactoring ایمن‌تر استفاده کنند
- تست و اعتبارسنجی را جدی‌تر بگیرند
- از ایجنت‌های کدنویسی به‌صورت کنترل‌شده و قابل بررسی استفاده کنند
- یادگیری برنامه‌نویسی را پروژه‌محورتر دنبال کنند

JumpLander قرار نیست جای برنامه‌نویس را بگیرد.

اصل اصلی این مسیر:

```text
AI suggests
→ Developer reviews
→ Tests validate
→ Code improves
```

یعنی هوش مصنوعی پیشنهاد می‌دهد، توسعه‌دهنده بررسی می‌کند، تست‌ها اعتبارسنجی می‌کنند، و در نهایت کد بهتر می‌شود.

---

## JumpLander در یک نگاه

**JumpLander** یک پروژه مهندسی هوش مصنوعی برای توسعه نرم‌افزار است.

تمرکز اصلی آن روی حوزه‌های زیر است:

- ابزارهای توسعه‌دهنده
- ایجنت‌های کدنویسی
- دیتاست‌های برنامه‌نویسی
- کمک به دیباگ
- کمک به refactoring
- توضیح کد
- آموزش برنامه‌نویسی
- پژوهش در حوزه AI-assisted software engineering
- منابع فارسی و انگلیسی برای برنامه‌نویسان

این راهنما یکی از اسناد آموزشی JumpLander برای توضیح جریان‌های کاری پیشنهادی در محیط‌های AI-assisted coding است.

---

## شروع سریع — اولین قدم‌ها در یک محیط AI-Assisted Coding

فرض کنید وارد یک محیط کدنویسی شده‌اید که در کنار ادیتور، یک دستیار هوش مصنوعی نیز دارد.

اولین قدم‌ها:

### 1. پروژه را مشخص کنید

قبل از استفاده از AI، محدوده پروژه را مشخص کنید:

- این پروژه با چه زبانی نوشته شده؟
- هدف پروژه چیست؟
- کدام فایل‌ها مهم‌تر هستند؟
- چه چیزی باید تغییر کند؟
- آیا تست وجود دارد؟
- آیا کد production است یا آموزشی؟

هرچه زمینه بهتر مشخص شود، خروجی AI قابل بررسی‌تر و دقیق‌تر خواهد بود.

---

### 2. هدف را دقیق بنویسید

به‌جای پرامپت‌های مبهم مثل:

```text
Make this better
```

بهتر است بنویسید:

```text
Refactor this function to reduce duplicated logic, keep the same behavior, and explain the changes in Persian.
```

یا:

```text
Review this file for possible bugs, security issues, and readability problems. Do not rewrite the code yet.
```

---

### 3. خروجی AI را مستقیم اعمال نکنید

هر پاسخی که AI تولید می‌کند باید بررسی شود.

قبل از استفاده:

- تغییرات را بخوانید
- منطق را بررسی کنید
- تست‌ها را اجرا کنید
- اگر وابستگی جدید اضافه شده، دلیلش را بپرسید
- اگر کد حساس است، دستی review کنید

---

## بخش‌های پیشنهادی یک پنل یا ابزار JumpLander

در یک نسخه کامل‌تر از ابزارهای JumpLander، می‌توان چنین بخش‌هایی را تصور کرد:

### 1. File Explorer

برای مرور فایل‌ها و پوشه‌های پروژه.

کاربردها:

- مشاهده ساختار پروژه
- انتخاب فایل هدف
- بررسی وابستگی بین فایل‌ها
- آماده‌سازی زمینه برای AI

---

### 2. Code Editor

محل اصلی ویرایش کد.

کاربردها:

- نوشتن و ویرایش کد
- انتخاب بخشی از کد برای توضیح یا refactor
- مشاهده تغییرات پیشنهادی
- مقایسه نسخه قبل و بعد

---

### 3. AI Chat / Assistant Panel

بخش گفت‌وگو با دستیار هوش مصنوعی.

کاربردها:

- توضیح کد
- تحلیل خطا
- پیشنهاد refactoring
- تولید نمونه تست
- بررسی معماری
- پاسخ به پرسش‌های برنامه‌نویسی
- تولید مستندات کوتاه

---

### 4. Terminal / Console

محل اجرای دستورات، تست‌ها و بررسی خروجی.

کاربردها:

- اجرای پروژه
- اجرای تست‌ها
- بررسی error logs
- نصب وابستگی‌ها
- مشاهده خروجی واقعی برنامه

---

### 5. Preview / Diff Viewer

برای مشاهده تغییرات پیشنهادی قبل از اعمال.

کاربردها:

- بررسی patch
- مقایسه نسخه قبلی و جدید
- رد یا قبول تغییرات
- جلوگیری از اعمال تغییرات خطرناک

---

## جریان‌های کاری پیشنهادی

### 1. توضیح کد

زمانی که یک فایل یا تابع را نمی‌فهمید، از AI برای توضیح کمک بگیرید.

پرامپت پیشنهادی:

```text
Explain this function in simple Persian. Focus on what it does, inputs, outputs, and possible risks.
```

خروجی مناسب باید شامل موارد زیر باشد:

- هدف تابع
- ورودی‌ها
- خروجی‌ها
- منطق اصلی
- نکات خطرناک یا مبهم
- پیشنهاد بهبود، اگر لازم باشد

---

### 2. تولید تابع جدید

برای تولید کد جدید، هدف، محدودیت و فرمت خروجی را دقیق مشخص کنید.

پرامپت پیشنهادی:

```text
Create a Python function called fast_prime that checks whether a number is prime. Keep it readable, add docstring, and include simple unit tests.
```

بعد از دریافت خروجی:

1. کد را بخوانید
2. تست‌ها را اجرا کنید
3. edge caseها را بررسی کنید
4. اگر لازم بود از AI بخواهید توضیح دهد
5. سپس کد را وارد پروژه کنید

---

### 3. Refactoring

Refactoring یعنی بهبود ساختار کد بدون تغییر رفتار اصلی.

پرامپت پیشنهادی:

```text
Refactor the selected code to improve readability and reduce duplicated logic. Do not change the external behavior. Explain the changes briefly.
```

قبل از اعمال تغییرات:

- تفاوت نسخه قدیم و جدید را بررسی کنید
- تست‌ها را اجرا کنید
- مطمئن شوید رفتار اصلی تغییر نکرده
- در صورت پروژه حساس، تغییرات را دستی review کنید

---

### 4. Debugging

برای دیباگ، فقط نگویید «این خطا را حل کن».

اطلاعات لازم را بدهید:

- پیام خطا
- فایل مربوطه
- ورودی‌ای که باعث خطا شده
- رفتار مورد انتظار
- رفتار واقعی
- محیط اجرا

پرامپت پیشنهادی:

```text
Analyze this error. Explain the likely cause, suggest debugging steps, and propose a safe fix. Do not rewrite the whole file unless necessary.
```

---

### 5. Security Review

برای بررسی امنیت، خروجی AI باید به‌عنوان پیشنهاد اولیه دیده شود، نه حکم قطعی.

پرامپت پیشنهادی:

```text
Review this code for common security risks such as SQL injection, XSS, unsafe file upload, exposed secrets, and weak validation. Explain each issue and suggest safer alternatives.
```

نکات مهم:

- کلیدهای API را داخل چت قرار ندهید
- اطلاعات کاربران را ماسک کنید
- کد امنیتی را دستی بررسی کنید
- پیشنهادهای AI را تست کنید
- برای پروژه حساس، از ابزارهای تخصصی امنیت هم استفاده کنید

---

### 6. Test Generation

AI می‌تواند برای تولید تست‌های اولیه کمک کند.

پرامپت پیشنهادی:

```text
Generate unit tests for this function. Include normal cases, edge cases, and invalid input cases.
```

بعد از دریافت تست‌ها:

- تست‌ها را اجرا کنید
- مطمئن شوید تست‌ها واقعاً رفتار درست را بررسی می‌کنند
- تست‌های بی‌ارزش یا صرفاً ظاهری را حذف کنید
- edge caseهای مهم را اضافه کنید

---

### 7. Documentation Generation

برای مستندسازی، AI می‌تواند توضیح کوتاه، README، docstring یا comment تولید کند.

پرامپت پیشنهادی:

```text
Write a clear README section for this module. Explain purpose, usage, inputs, outputs, and limitations.
```

مستندات خوب باید:

- دقیق باشد
- اغراق نکند
- محدودیت‌ها را بگوید
- برای کاربر قابل اجرا باشد
- مثال واقعی داشته باشد

---

## جریان کاری ایجنت‌های کدنویسی

ایجنت‌های کدنویسی باید چندمرحله‌ای، قابل کنترل و قابل بررسی باشند.

یک جریان سالم:

```text
Analyze
→ Plan
→ Propose Changes
→ Preview Diff
→ Developer Review
→ Apply
→ Test
→ Report
```

توضیح مراحل:

### Analyze

ایجنت فایل‌ها، ساختار پروژه و مسئله را بررسی می‌کند.

### Plan

قبل از تغییر کد، یک برنامه کوتاه ارائه می‌دهد.

### Propose Changes

تغییرات پیشنهادی را به‌صورت patch یا توضیح ساختاری ارائه می‌کند.

### Preview Diff

توسعه‌دهنده تغییرات را قبل از اعمال بررسی می‌کند.

### Developer Review

هیچ تغییر مهمی نباید بدون review اعمال شود.

### Apply

تغییرات تأییدشده اعمال می‌شوند.

### Test

تست‌ها یا دستورهای لازم اجرا می‌شوند.

### Report

ایجنت خلاصه می‌دهد:

- چه چیزی تغییر کرد
- چرا تغییر کرد
- چه تستی اجرا شد
- چه ریسکی باقی مانده

---

## میانبرهای پیشنهادی برای ابزارهای آینده

این میانبرها می‌توانند برای طراحی آینده ابزارهای JumpLander استفاده شوند:

| Shortcut | Action |
| :--- | :--- |
| `Ctrl + Enter` | ارسال پرامپت به دستیار |
| `Ctrl + Space` | پیشنهاد تکمیل کد |
| `Ctrl + .` | نمایش Quick Fix |
| `Ctrl + S` | ذخیره فایل |
| `Alt + Enter` | اجرای اکشن روی selection |
| `Ctrl + Shift + R` | درخواست Refactor |
| `Ctrl + Shift + E` | توضیح کد انتخاب‌شده |
| `Ctrl + Shift + T` | تولید تست پیشنهادی |

---

## نکات پرامپت‌نویسی

### 1. هدف را روشن بنویسید

ضعیف:

```text
Fix this
```

بهتر:

```text
Find the cause of this error and suggest a minimal fix without changing unrelated code.
```

---

### 2. محدودیت مشخص کنید

مثال:

```text
Do not add new dependencies.
```

یا:

```text
Keep the solution under 80 lines.
```

یا:

```text
Use plain JavaScript only.
```

---

### 3. خروجی مورد انتظار را مشخص کنید

مثال:

```text
Return the answer as:
1. Problem summary
2. Cause
3. Suggested fix
4. Test cases
```

---

### 4. از AI بخواهید توضیح بدهد

مثال:

```text
Explain the change in 3 short Persian bullet points.
```

---

### 5. از پرامپت‌های چندمرحله‌ای استفاده کنید

برای کارهای بزرگ، همه چیز را یک‌جا نخواهید.

بهتر است مرحله‌ای جلو بروید:

```text
First analyze the code. Do not change anything yet.
```

بعد:

```text
Now propose a refactoring plan.
```

بعد:

```text
Generate the patch only for the selected function.
```

---

## پرامپت‌های آماده

### تولید کد

```text
Generate a REST API endpoint in Node.js with Express for user login. Include input validation, JWT generation, and clear error handling. Do not use unnecessary dependencies.
```

---

### توضیح کد

```text
Explain this function in simple Persian. Include purpose, inputs, outputs, and possible edge cases.
```

---

### Refactoring

```text
Refactor the selected code to improve readability and testability. Keep the same behavior and explain the changes briefly.
```

---

### دیباگ

```text
Analyze this error message and code. Explain the likely cause, suggest debugging steps, and propose a minimal safe fix.
```

---

### امنیت

```text
Scan this code for common security issues such as SQL injection, XSS, unsafe file handling, exposed secrets, and weak validation. Explain risks and suggest safer alternatives.
```

---

### تست

```text
Generate unit tests for this function. Include normal cases, edge cases, and invalid input cases.
```

---

### مستندسازی

```text
Write a README section for this module. Explain what it does, how to use it, limitations, and a simple example.
```

---

## بهترین روش‌ها

برای استفاده حرفه‌ای از AI در برنامه‌نویسی:

- قبل از اعمال تغییرات، diff را بررسی کنید
- قبل از کارهای بزرگ، commit بگیرید
- خروجی AI را بدون تست وارد پروژه نکنید
- secrets و اطلاعات حساس را ارسال نکنید
- برای کدهای امنیتی، بررسی انسانی ضروری است
- تغییرات کوچک و قابل کنترل انجام دهید
- از AI توضیح بخواهید، نه فقط کد
- تست را بخشی از جریان کاری کنید
- محدودیت‌ها را در پرامپت مشخص کنید
- از پرامپت‌های مرحله‌ای استفاده کنید

---

## خطاهای رایج کاربران

### 1. درخواست خیلی کلی

مثال ضعیف:

```text
Make my project better
```

مشکل: خروجی نامتمرکز و غیرقابل بررسی می‌شود.

---

### 2. اعمال مستقیم کد AI

مشکل: ممکن است باگ، تغییر رفتار یا مشکل امنیتی ایجاد شود.

---

### 3. ارسال اطلاعات حساس

مشکل: کلید API، رمز، اطلاعات کاربران و داده‌های حساس نباید وارد چت شوند.

---

### 4. نداشتن تست

مشکل: بدون تست نمی‌توان فهمید تغییرات واقعاً درست هستند یا نه.

---

### 5. وابستگی بیش از حد به AI

مشکل: توسعه‌دهنده باید منطق را بفهمد، نه اینکه فقط خروجی را کپی کند.

---

## عیب‌یابی سریع

### اگر خروجی AI اشتباه بود

- مسئله را دقیق‌تر توضیح دهید
- فایل یا خط مربوطه را مشخص کنید
- محدودیت‌ها را اضافه کنید
- از مدل بخواهید فقط تحلیل کند، نه بازنویسی
- خروجی را با تست بررسی کنید

---

### اگر کد بعد از تغییر خراب شد

- آخرین تغییر را با diff بررسی کنید
- تست‌ها را اجرا کنید
- به commit قبلی برگردید
- تغییر را کوچک‌تر کنید
- از AI بخواهید فقط علت را تحلیل کند

---

### اگر پاسخ خیلی طولانی بود

از پرامپت کوتاه‌تر استفاده کنید:

```text
Answer in 5 bullet points only.
```

---

### اگر پاسخ بیش از حد کلی بود

محدودیت اضافه کنید:

```text
Focus only on performance issues in this function.
```

---

## نکات امنیتی و حریم خصوصی

برای استفاده امن‌تر از AI:

- کلید API ارسال نکنید
- رمزها را حذف یا ماسک کنید
- اطلاعات کاربران را anonymize کنید
- فایل‌های حساس را کامل وارد چت نکنید
- کد تولیدشده را review کنید
- دسترسی ابزارها را محدود نگه دارید
- برای اجرای کد ناشناس از محیط ایزوله استفاده کنید
- خروجی AI را منبع قطعی امنیت ندانید

---

## جایگاه این راهنما در JumpLander

این راهنما می‌تواند در بخش‌های زیر استفاده شود:

- مستندات JumpLander
- JumpLander AI Academy
- GitHub README
- مقاله آموزشی
- صفحه راهنمای ابزارهای آینده
- محتوای فارسی برای برنامه‌نویسان
- منبع اولیه برای طراحی UX ایجنت‌های کدنویسی

---

## لینک‌های رسمی JumpLander

- Website: https://jumplander.org
- Persian Homepage: https://jumplander.org/fa/home
- Documentation: https://jumplander.org/fa/docs
- Blog: https://jumplander.org/fa/blogs
- JumpPedia / Forum: https://jumplander.org/fa/forum
- FAQ: https://jumplander.org/fa/FAQ
- About: https://jumplander.org/fa/about
- Contact: https://jumplander.org/fa/contact
- Support: https://jumplander.org/fa/rate
- Hugging Face: https://huggingface.co/jumplander
- GitHub: https://github.com/jumplander-readme

---

## جمع‌بندی

استفاده حرفه‌ای از هوش مصنوعی در برنامه‌نویسی یعنی:

```text
شفاف نوشتن مسئله
→ دریافت پیشنهاد
→ بررسی انسانی
→ تست و اعتبارسنجی
→ اعمال کنترل‌شده
→ مستندسازی تغییرات
```

JumpLander در مسیر ساخت ابزارها، مستندات، دیتاست‌ها و جریان‌های کاری است که این مدل استفاده از AI را برای توسعه‌دهندگان روشن‌تر، امن‌تر و کاربردی‌تر کند.

**JumpLander — زیرساخت عملی برای برنامه‌نویسی با کمک هوش مصنوعی.**
