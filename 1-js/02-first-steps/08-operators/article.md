# عملگرهای ساده، ریاضیات

ما عملگرهای مختلفی را از زمان مدرسه به خاطر داریم. مانند جمع `+`، تفریق `-`، ضرب `*` و دیگر عملگرها. 

در این فصل، ما با عملگرهای ساده شروع می‌کنیم، سپس روی موضوعات مخصوص جاوااسکریپت تمرکز می‌کنیم که توسط دروس محاسباتی در مدرسه پوشش داده نشده‌اند.

## اصطلاحات: یگانه (unary) - دوگانه (binary) - عملوند (operand)

پیش از ادامه بیایید مفهوم این اصطلاحات را بفهمیم.

- *عملوند* -- همان چیزی است که عملگرها بر روی آنها اعمال می‌شوند. برای نمونه در ضرب 5 * 2 دو عملوند داریم: عملوند سمت چپ 2 و عملوند سمت راست 5 است. برخی به جای "عملوند" آن را "آرگومان" نیز می‌خوانند.
- یک عملگر زمانی unary است که فقط یک عملوند داشته باشد. برای نمونه منفی کننده‌ی یگانه `-` که علامت یک عدد را برعکس می‌کند:

    ```js run
    let x = 1;

    *!*
    x = -x;
    */!*
    alert( x ); // -1، منفی کننده‌ی یگانه اعمال شد
    ```
- یک عملگر زمانی binary است که دو عملوند داشته باشد. همان عملگر منفی کننده در شکل دوگانه هم وجود دارد:
    
    ```js run no-beautify
    let x = 1, y = 3;
    alert( y - x ); // 2، عملگر دوگانه منفی که مقدارها را کم می‌کند
    ```

    در اصل در مثال‌های بالا دو عملگر مجزا داریم که نماد یکسانی دارند: اولی عملگر یگانه منفی کننده که علامت عدد را برعکس می‌کرد و دیگری عملگر دوگانه تفریق که یک عدد را از دیگری کم می‌کرد.

## ریاضیات

عملیات‌های ریاضی زیر پشتیبانی می‌شوند:

- جمع‌کردن `+`,
- تفریق‌کردن `-`,
- ضرب‌کردن `*`,
- تقسیم‌کردن `/`,
- باقی‌مانده `%`,
- بتوان‌رساندن `**`.

چهارتای اول سرراست هستند، در حالی که `%` و `**` نیاز به توضیح بیشتری دارند.

### باقی‌مانده %

عملگر باقی‌مانده `%`، بر خلاف ظاهرش، به درصد ارتباطی ندارد.

نتیجهٔ `a % b` [باقی‌مانده](https://en.wikipedia.org/wiki/Remainder) تقسیم `a` بر `b` است. 

برای مثال:

```js run
alert( 5 % 2 ); // ۱، باقی‌ماندهٔ تقسیم ۵ بر ۲
alert( 8 % 3 ); // ۲، باقی‌ماندهٔ تقسیم ۸ بر ۳
```

### بتوان‌رساندن **

عملگر بتوان‌رساندن `a**b` `a` را بتوانِ `b` می‌رساند.

در ریاضیات مدرسه، ما آن را به صورت a<sup>b</sup> می‌نویسیم.

برای مثال:

```js run
alert( 2 ** 2 ); // 2² = 4
alert( 2 ** 3 ); // 2³ = 8
alert( 2 ** 4 ); // 2⁴ = 16
```

درست مانند ریاضیات، عملگر بتوان‌رساندن برای اعداد غیر صحیح نیز تعریف می‌شود.

برای مثال، جذر(ریشهٔ دوم) یک عدد با بتوان‌رساندن آن به ½ به‌دست می‌آید: 

```js run
alert( 4 ** (1/2) ); // 2 (بتوان ۱/۲ با جذر آن برابر است.)
alert( 8 ** (1/3) ); // 2 (بتوان ۱/۳ با ریشهٔ سوم آن برابر است.)
```


## تلفیق رشته‌ها با عملگر دوگانه +

بیایید ویژگی‌های عملگرهای جاوااسکریپت که فراتر از دروس محاسباتی مدرسه است را ببینیم.

معمولا از عملگر + برای جمع اعداد استفاده می‌شود.

اما زمانی که این عملگر روی رشته‌ها اعمال شود، آنها را ادغام می‌کند.

```js
let s = "my" + "string";
alert(s); // mystring
```

در نظر داشته باشید که اگر یکی از عملوندها string باشد، دیگری نیز به string تبدیل می‌شود.

برای نمونه:

```js run
alert( '1' + 2 ); // "12"
alert( 2 + '1' ); // "21"
```

همانطور که می‌بینید، مهم نیست که عملوند اول string باشد یا عملوند دوم.

یک مثال پیچیده‌تر:

```js run
alert(2 + 2 + '1' ); // "نتیجه "41" می‌شود نه "221
```

اینجا، عملگرها یکی پس از دیگری کار می‌کنند. اولین `+` دو عدد را جمع می‌کند، پس `4` را برمی‌گرداند، سپس `+` دوم رشته‌ی `1` را به آن اضافه می‌کند، پس مثل این است که بنویسیم `'41' = '1' + 4`.

```js run
alert('1' + 2 + 2); // "نتیجه "122" می‌شود نه "14
```
اینجا، اولین عملوند یک string است، کامپایلر با دو عملوند دیگر هم مانند string رفتار می‌کند. `2` با `'1'` ادغام می‌شود، پس مانند این است که بنویسیم `"12" = 2 + '1'` و سپس `"122" = 2 + "12"`.

عملگر دوگانه `+` تنها عملگری است که با رشته‌ها اینگونه رفتار می‌کند. عملگرهای محاسباتی دیگر تنها با اعداد کار می‌کنند و همیشه عملوندهای خود را به عدد تبدیل می‌کنند.

اینجا یک دمو برای تفریق و تقسیم وجود دارد:

```js run
alert( 2 - '1' ); // 1
alert( '6' / '2' ); // 3
```

## تبدیل به عدد، عملگر + یگانه

علامت جمع + به دو شکل وجود دارد: به صورت عملگر دوگانه که بالاتر از آن استفاده کردیم و به صورت عملگر یگانه.

عملگر + یگانه، یا به عبارتی دیگر عملگر `+` که روی یک مقدار اعمال می‌شود، کاری روی اعداد انجام نمی‌دهد. اما اگر عملوند عدد نباشد، عملگر + یگانه آن را به عدد تبدیل می‌کند.

برای نمونه:

```js run
// تأثیری روی اعداد ندارد
let x = 1;
alert( +x ); // 1

let y = -2;
alert( +y ); // -2

*!*
// مقدار غیر عددی را تبدیل می‌کند
alert( +true ); // 1
alert( +"" );   // 0
*/!*
```

در واقع این همان کاریست که `Number(...)` انجام می‌دهد ولی به شکلی کوتاه‌تر.

نیاز به تبدیل رشته به عدد اغلب پیش می‌آید. برای نمونه اگر در حال دریافت مقادیری از فرم‌های HTML باشیم، آنها معمولا رشته هستند. اگر بخواهیم آنها را جمع کنیم چه کار باید کنیم؟

عملگر + دوگانه به صورت string آنها را بهم اضافه می‌کند:

```js run
let apples = "2";
let oranges = "3";

alert( apples + oranges ); // "23" ،عملگر + دوگانه رشته‌ها را ادغام می‌کند
```

اگر خواستیم با آنها مانند عدد برخورد کنیم، باید آنها را به عدد تبدیل کرده و سپس آنها را جمع می‌کنیم:

```js run
let apples = "2";
let oranges = "3";

*!*
// هر دو مقدار قبل از عملگر + دوگانه به عدد تبدیل شدند
alert( +apples + +oranges ); // 5
*/!*

// شکل طولانی‌تر
// alert( Number(apples) + Number(oranges) ); // 5
```

از دیدگاه یک ریاضی‌دان، تعداد زیاد علامت + ممکن است عجیب به نظر برسد، اما از دیدگاه یک برنامه‌نویس اینطور نیست: عملگرهای + یگانه اول اعمال می‌شوند و رشته‌ها را به عدد تبدیل می‌کنند و سپس عملگر + دوگانه اعداد را با هم جمع می‌کند.

چرا عملگرهای + یگانه قبل از دوگانه روی مقدارها اعمال شدند؟ همانطور که خواهیم دید، به خاطر *اولویت بالاتر* آنها است.

## اولویت عملگرها

اگر در یک عبارت بیش از یک عملگر وجود داشته باشد، ترتیب اجرای آنها بر اساس اولویت آنها خواهد بود، یا به عبارتی دیگر، بر اساس ترتیب تقدم پیش فرض عملگرها.

از زمان مدرسه همه ما می‌دانیم که در عبارت `1 + 2 * 2` ابتدا عمل ضرب انجام می‌شود و سپس عمل جمع. این همان اولویت عملگرها است. اینکه عمل ضرب *اولویت بالاتری* نسبت به جمع دارد.

پرانتزها بر هر اولویتی، اولویت دارند پس زمانی که از ترتیب پیش فرض عملگرها راضی نیستیم، می‌توانیم با پرانتزها این اولویت را تغییر دهیم. برای مثال، بنویسیم `(1 + 2) * 2`.

عملگرهای مختلفی در جاوااسکریپت وجود دارد و هر کدام اولویت مربوط به خود را دارا می‌باشند. عملگری که اولویت بالاتری داشته باشد اول اجرا می‌شود. همینطور اگر دو عملگر عدد یکسانی داشتند اولویت اجرا از چپ به راست (در کد) می‌باشد.

اینجا یک خلاصه‌ای از [جدول اولویت بندی](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence) داریم (شما نیازی به حفظ این جدول ندارید، اما توجه داشته باشید که عملگرهای یگانه اولویت بالاتری نسبت به عملگر دوگانه نظیر خود دارند):

| اولویت | نام | علامت |
|------------|------|------|
| ... | ... | ... |
| 17 | جمع یگانه | `+` |
| 17 | تفریق یگانه | `-` |
| 16 | بتوان رساندن | `**` |
| 15 | ضرب | `*` |
| 15 | تقسیم | `/` |
| 13 | جمع | `+` |
| 13 | تفریق | `-` |
| ... | ... | ... |
| 3 | مقدارده | `=` |
| ... | ... | ... |

همانطور که می‌بینیم "عملگر + یگانه" اولویت 17 دارد که از عملگر جمع ( + دوگانه) با اولویت 13 بالاتر است. به همین دلیل است که در عبارت `"+apples + +oranges"` عملگرهای + یگانه پیش از علامت جمع اجرا می‌شوند.

## مقداردهی

در نظر داشته باشید که مقداردهی با علامت `=` نیز یک عملگر است. در جدول اولویت‌ها با اولویت پایین `3` قرار گرفته است.

به همین دلیل است که وقتی متغیری را مقدار دهی می‌کنیم، مانند `x = 2 * 2 + 1`، ابتدا عملیات محاسباتی انجام شده و سپس مقداردهی `=` صورت می‌گیرد و نتیجه را داخل `x` ذخیره می‌کند. 

```js
let x = 2 * 2 + 1;

alert( x ); // 5
```

### عملگر = یک مقدار را باز می‌گرداند

این موضوع که `=` یک اپراتور باشد نه یک ساختار "جادویی" در زبان، دلیل جالبی دارد.

تمامی عملگرها در جاوااسکریپت یک مقدار برمی‌گردانند. این موضوع برای `+` و `-` بدیهی است، اما برای `=` هم صدق می‌کند.

عبارت `x = value` ابتدا `value` را در `x` می‌نویسد و *سپس آن را باز می‌گرداند*.

در اینجا یک نمونه از مقداردهی به عنوان بخشی از یک عبارت پیچیده‌تر را داریم:

```js run
let a = 1;
let b = 2;

*!*
let c = 3 - (a = b + 1);
*/!*

alert( a ); // 3
alert( c ); // 0
```

در مثال بالا، نتیجه عبارت `(a = b + 1)` مقداری است که به `a` مقداردهی شده‌است (برابر با `3`). پس از آن `a` برای ارزیابی بیشتر استفاده می‌شود.

کد جالبی‌ست. ما باید طرز کار آن را یاد بگیریم تا زمانی که در کدهای کتابخانه‌های مختلف با آن روبرو می‌شویم بدانیم که چطور کار می‌کند. 

ولی نباید به این شکل برنامه‌نویسی کنیم چراکه کدهای ما را ناخوانا و نامرتب می‌کند.

### مقداردهی زنجیره‌ای

یک ویژگی جالب دیگر قابلیت زنجیره‌ای کردن مقداردهی‌ها است:

```js run
let a, b, c;

*!*
a = b = c = 2 + 2;
*/!*

alert( a ); // 4
alert( b ); // 4
alert( c ); // 4
```

مقداردهی‌های زنجیره‌ای از راست به چپ ارزیابی می‌شوند. ابتدا، راست ترین عبارت `2 + 2` ارزیابی شده و سپس به متغیرهای سمت چپ تخصیص داده می‌شود: `c`، `b` و `a`. سرانجام، تمام متغیرها یک مقدار دارند.

یک بار دیگر ذکر می‌کنیم، بهتر است که برای خوانایی، چنین کدی را به چند خط تقسیم کنید:

```js
c = 2 + 2;
b = c;
a = c;
```
این کد برای خواندن راحت‌تر است، مخصوصا وقتی به سرعت با چشم‌هایمان کد را بررسی می‌کنیم.

## تغییر دادن در محل

ما اغلب اوقات نیاز داریم که یک عملگر را روی متغیری اعمال کنیم و نتیجه جدید را داخل همان متغیر ذخیره کنیم.

برای مثال:

```js
let n = 2;
n = n + 5;
n = n * 2;
```

این شکل کد نویسی می‌تواند با استفاده از عملگرهای `=+` و `=*` کوتاه شود:

```js run
let n = 2;
n += 5; // (یکسان است n = n + 5 با) است n = 7 حالا
n *= 2; // (یکسان است n = n * 2 با) است n = 14 حالا

alert( n ); // 14
```

عملگرهای کوتاه "تغییر و مقداردهی" برای همه‌ی عملگرهای محاسباتی و بیتی (bitwise) وجود دارند: `=/`، `=-` و غیره.

چنین عملگرهایی اولویتی مشابه با عملگر مقداردهی معمولی دارند، پس آنها بعد از اکثر عملیات‌ها اجرا می‌شوند:

```js run
let n = 2;

n *= 3 + 5;

alert( n ); // 16 (یکسان است n *= 8، قسمت سمت راست اول ارزیابی می‌شود)
```

## عملگر افزایش/کاهش 

<!-- Can't use -- in title, because built-in parse turns it into – -->

افزایش یا کاهش یک عدد به اندازه یک واحد در بین متداول‌ترین عملیات‌های عددی هستند.

بنابراین عملگرهای خاصی برای این موضوع وجود دارند:

- **عملگر افزایش** `++` که یک واحد به عدد اضافه می‌کند:

    ```js run no-beautify
    let counter = 2;
    counter++;        // عمل می‌کند اما کوتاه‌تر است counter = counter + 1 درست مانند
    alert( counter ); // 3
    ```
- **عملگر کاهش** `--` که یک واحد از عدد کم می‌کند:

    ```js run no-beautify
    let counter = 2;
    counter--;        // عمل می‌کند اما کوتاه‌تر است counter = counter - 1 درست مانند
    alert( counter ); // 1
    ```

```warn
این عملگرها فقط بر روی متغیرها اعمال می‌شوند و برای نمونه `++5` با خطا مواجه خواهد شد.
```

عملگرهای `++` و `--` می‌توانند پیش و پس از متغیر قرار گیرند.

- وقتی پس از متغیر قرار بگیرد "شکل پسوندی" دارد: `counter++`.
- وقتی پیش از متغیر قرار گیرد "شکل پیشوندی" دارد: `++counter`.

هردو گزاره، کار یکسانی می‌کنند: به `counter` `یکی` اضافه می‌کنند.

آیا تفاوتی بین آنها وجود دارد؟ بله، اما فقط با مشاهده‌ی مقدار باز گردانده شده از `--/++`، می‌توانیم این تفاوت را دریابیم.

بیایید موضوع را روشن کنیم. همانطور که همه ما می‌دانیم، تمام عملگرها مقداری برمی‌گردانند. عملگرهای افزایش/کاهش هم این کار را انجام می‌دهند. شکل پیشوندی، مقدار جدید را برمی‌گرداند درحالیکه شکل پسوندی مقدار قبلی را برمی‌گرداند (قبل از افزایش/کاهش).

برای اینکه تفاوت را ببینید، این مثال کمک می‌کند:

```js run
let counter = 1;
let a = ++counter; // (*)

alert(a); // *!*2*/!*
```

در خط `(*)` شکل *پیشوندی* `++counter` متغیر `counter` را یک واحد افزایش می‌دهد و مقدار جدید `2` را برمی‌گرداند. در نتیجه `alert` مقدار `2` را نمایش می‌دهد.

حالا بیایید از شکل پسوندی استفاده کنیم:

```js run
let counter = 1;
let a = counter++; // (*) تغییر دادیم counter++ را به ++counter

alert(a); // *!*1*/!*
```

در خط `(*)` شکل پسوندی `counter++` مقدار `counter` را یک واحد افزایش می‌دهد ولی مقدار قبلی این متغیر را برمی‌گرداند (قبل از افزایش). در نتیجه `alert` مقدار `1` را نمایش می‌دهد.

به طور خلاصه:

- اگر مقدار بازگشتی از عملگرهای افزایش و کاهش مورد استفاده قرار نگیرد، تفاوتی در استفاده از آنها وجود ندارد:

    ```js run
    let counter = 0;
    counter++;
    ++counter;
    alert( counter ); // 2 ،خطوط بالا کار مشابهی انجام دادند
    ```
    - اگر می‌خواهیم مقداری را افزایش داده *و* بلافاصله از نتیجه عملگر استفاده نماییم، باید از شکل پیشوندی استفاده کنیم:

    ```js run
    let counter = 0;
    alert( ++counter ); // 1
    ```
    - اگر می‌خواهیم مقداری را افزایش داده و از مقدار قبلی آن استفاده نماییم باید از شکل پسوندی استفاده کنیم:
    
    ```js run
    let counter = 0;
    alert( counter++ ); // 0
    ```

````smart header="عملگرهای افزایش و کاهش در بین دیگر عملگرها"
عملگرهای `--/++` در عبارات (expressions) نیز قابل استفاده هستند. اولویت آنها از اکثر عملگرهای ریاضیاتی بالاتر است.

برای نمونه:

```js run
let counter = 1;
alert( 2 * ++counter ); // 4
```

در مقایسه با:

```js run
let counter = 1;
alert( 2 * counter++ ); // 2 ،مقدار «قدیمی» را برمی‌گرداند counter++ چون
```

با اینکه از نظر فنی مشکلی ندارد ولی چنین روشی خوانایی کد را کاهش می‌دهد. اینکه یک خط کارهای مختلفی انجام می‌دهد مناسب نیست.

در هنگام خواندن کدها، چشم‌ها به صورت عمودی و با سرعت کدها را می‌خوانند و چیزی مانند `counter++` به سادگی از چشم پنهان می‌ماند و دیگر واضح نخواهد بود که متغیر افزایش پیدا کرده است.

ما پیشنهاد می‌کنیم هر عمل را در یک خط بنویسید:

```js run
let counter = 1;
alert( 2 * counter );
counter++;
```
````

## عملگرهای بیتی

عملگرهای بیتی با آرگومان‌ها به شکل اعداد صحیح 32 بیتی رفتار می‌کنند و در سطح نمایش دودویی با آنها کار می‌کنند. 

این عملگرها فقط برای جاوااسکریپت نیستند و در اکثر زبان‌های برنامه نویسی پشتیبانی می‌شوند.

لیست عملگرها:

- AND ( `&` )
- OR ( `|` )
- XOR ( `^` )
- NOT ( `~` )
- LEFT SHIFT ( `<<` )
- RIGHT SHIFT ( `>>` )
- ZERO-FILL RIGHT SHIFT ( `>>>` )

این عملگرها بسیار به ندرت استفاده می‌شوند، زمانی که بخواهیم با اعداد در پایین‌ترین سطح خود (bitwise) کار کنیم. ما فعلا به این عملگرها نیازی نداریم، همانطور که در توسعه وب استفاده‌ی بسیار کمی از آنها دارد، اما در بعضی حوزه‌های خاص مانند کریپتوگرافی، این عملگرها مفید هستند. شما می‌توانید فصل [عملگرهای بیتی](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Bitwise) را در MDN هر زمان که نیاز داشتید بخوانید.

## کاما

عملگر `,` یکی از نادرترین و غیرمعمول ترین عملگر‌هاست. بعضی اوقات، برای نوشتن کد کوتاه‌تر استفاده می‌شود پس ما نیاز داریم که متوجه بشویم که چه اتفاقی در حال رخ دادن است.

این عملگر به ما اجازه ارزیابی چندین عبارت را می‌دهد که با یک کاما از یکدیگر جدا می‌شوند. هر کدام از آنها هم محاسبه و ارزیابی می‌شود اما تنها نتیجه آخری برگردانده می‌شود.

به عنوان مثال:

```js run
*!*
let a = (1 + 2, 3 + 4);
*/!*

alert( a ); // 7 (3 + 4 نتیجه‌ی)
```

اولین عبارت `2 + 1` محاسبه می‌شود و جوابش دور ریخته می‌شود. سپس، `4 + 3` محاسبه می‌شود و به عنوان نتیجه بازگردانده می‌شود.

```smart header="کاما اولیویت بسیار کمی دارد"
توجه داشته باشید که عملگر کاما اولویت بسیار کمی دارد، کمتر از `=`، بنابراین پرانتزها در مثال بالا مهم هستند.

بدون آنها: `a = 1 + 2, 3 + 4` اول عملگر `+` را محاسبه می‌کند، یعنی نتیجه می‌شود `a = 3, 7`، سپس عملگر `=` باعث می‌شود که `a = 3` و بقیه‌ی عبارت پردازش نمی‌شود. یعنی چیزی شبیه این عبارت `(a = 1 + 2), 3 + 4`. 
```

چرا عملگری نیاز داریم که هرچیزی را به جز قسمت آخر دور میریزد؟

بعضی اوقات، در ساختارهای پیچیده برای انجام عمل‌های متعددی در یک خط استفاده می‌شود.

برای نمونه:

```js
// سه عملگر در یک خط
for (*!*a = 1, b = 3, c = a * b*/!*; a < 10; a++) {
 ...
}
```

چنین ترفندهایی در frameworkهای جاوااسکریپت خیلی استفاده می‌شوند. به همین علت است که آنها را ذکر می‌کنیم. اما عموما، خوانایی کد را بهبود نمی‌بخشند بنابراین قبل از استفاده کردن آنها باید فکر کنیم.
