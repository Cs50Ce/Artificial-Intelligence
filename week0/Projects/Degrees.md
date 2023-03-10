## تمرین Degrees
برنامه ای بنویسید که کوتاهترین مسیر واسطه بین دو بازیگر را محاسبه کند.
```
$ python degrees.py large 
Loading data... 
Data loaded. 
Name: Emma Watson
Name: Jennifer Lawrence 
3 degrees of separation. 
1: Emma Watson and Brendan Gleeson starred in Harry Potter and the Order of the Phoenix 
2: Brendan Gleeson and Michael Fassbender starred in Trespass Against Us 
3: Michael Fassbender and Jennifer Lawrence starred in X-Men: First Class
```
### پیش زمینه
طبق بازی شش درجۀ کوین بیکن (Six Degrees of Kevin Bacon)، هر فردی در صنعت فیلمسازی هالیوود میتواند،
طی شش مرحله، به کوین بیکن وصل شود؛ هر مرحله شامل پیدا کردن فیلمی می شود که هر دو بازیگر، در آن بازی کرده
باشند.
در این مسئله، میخواهیم کوتاه ترین مسیر بین دو بازیگر را با انتخاب مجموعه ای از فیلم ها که این دو را بهم وصل میکند،
پیدا کنیم. برای مثال، کوتاه ترین مسیر بین جنیفر لارنس و تام هنکس 2 است: جنیفر لارنس و کوین بیکن با بازی در فیلم
عه X-Men: First Class و کوین بیکن و تام هنکس نیز با بازی در فیلم Apollo 13 بهم وصل میشوند.
میتوانیم این موضوع را به صورت مسئلۀ جستجو درآوریم: حالت های ما افراد هستند. عمل های ما فیلم ها هستند که ما را از
یک بازیگر به بازیگر دیگر میبرند (درست است که یک فیلم می تواند ما را به چند بازیگر مختلف ببرد اما این امر مشکلی
برای مسئله فعلی ایجاد نمی کند). حالت اولیه و حالت نهایی ما توسط دو نفری که سعی داریم آ نها را بهم وصل کنیم تعیین
میشوند. با استفاده از جستجوی اول سطح، می توانیم کوتاه ترین مسیر از یک بازیگر به بازیگر دیگر را پیدا کنیم.


### توضیح
این کد توزیع حاوی مجموعه ای از فایل های CSV است: یک مجموعه در دایرکتوری(فولدر) large (بزرگ) و یک مجموعه
در دایرکتوری small (کوچک) قرار گرفته است. هر دو حاوی فایل هایی با نام ها و ساختارهای یکسان هستند اما small،
مجموعه دادۀ بسیار کوچک تری را به منظور تسهیل آزمون و آزمایش فراهم میکند.
هر مجموعه داده متشکل از سه فایل CSV است. اگر با فایل CSV آشنایی ندارید، باید بگوییم که این فایل صرفاً راهی برای
سازما ندهی داده ها با فرمت متنی است: هر ردیف متناظر با یک نمونه داده (Data entry) است که با علامت ویرگول
مقادیر آن نمونه از یکدیگر جدا می شوند.
فایل people.csv که در پوش هی small قرار دارد را باز کنید. مشاهده می کنید که هر فرد دارای یک شناسه منحصر به فرد
عه (id) است که با شناسه ی وی در پایگاه دادۀ IMDb مطابقت دارد. همچنین هر فرد دارای نام (name) و سال تولد (birth)
است.

سپس، فایل movies.csv را باز کنید. در اینجا میبینید که هر فیلم نیز دارای یک شناسهی منحصر به فرد (id)، بهعلاوۀ
عنوان (title) و سال انتشار فیلم (year) است.
حال فایل stars.csv را باز کنید. این فایل، بین افراد فایل people.csv و فیلم های فایل movies.csv ، رابطه برقرار
میکند. در هر ردیف، جفتی از مقادیر متناظر با person_id و movie_id وجود دارد. برای مثال، ردیف اول (صر فنظر از
سرستون ها)، مشخص میکند که فردی با شناسۀ 102 در فیلمی با شناسۀ 104257 بازی کرده است. با چک کردن آ نها
با فایلهای people.csv و movies.csv درمییابید که این خط میگوید که کوین بیکن در فیلم A Few Good Men
بازی کرده است.

سپس، فایل degrees.py را ببینید. در بالا، چند ساختمان داده برای ذخیرۀ اطلاعات از روی فایلهای CSV تعریف شده
است. دیکشنری names راهی برای جستجوی افراد بر اساس نام است: این دیکشنری، اسامی را به مجموع های از شناسه های
متناظر وصل میکند (زیرا ممکن است چند بازیگر، نامی یکسان داشته باشند). دیکشنری people ، شناسۀ هر فرد را به
دیکشنری دیگری وصل میکند که مقادیر name ، birth و مجموعۀ تمامی فیلم هایی را که در آ نها بازی کرده است
و (movies) در برمیگیرد. دیکشنری movies ، شناسۀ هر فیلم را به دیکشنری دیگری وصل میکند که مقادیر عنوان آن
فیلم (title)، سال انتشار (year) و مجموعۀ تمامی بازیگران آن فیلم (stars) را در خود جای داده است. تابع load_data،
داده ها را از روی فایلهای CSV در این ساختمان داده ها بارگیری میکند.

تابع main (اصلی) در این برنامه، ابتدا داده ها را در حافظه بارگیری میکند (دایرکتوری مورد نظر برای بارگیری داده ها را
میتوان به وسیلۀ یک آرگومان خط فرمان) Command-line argument معین کرد. سپس، تابع از کاربر میخواهد که
دو اسم تایپ کند. تابع person_id_for_name ، شناسۀ افراد را بازیابی میکند (و در صورتی که چند نفر اسامی یکسان
داشتند، از کاربر میخواهد تا شفافسازی کند که کدام بازیگر را مد نظر داشته است). سپس، در تابع main ، تابع
عه shortest_path را فرا خوانی میشود تا کوتاهترین مسیر واسطه بین این دو نفر را محاسبه و چاپ کند.
اما تابع shortest_path پیاده سازی نشده است. اینجا شما وارد عمل می شوید!


### معیارها
برخی ابزارهای خودکار، در اِعمال محدودیت های مطرح شده در معیارهای زیر، به اعضای تیم کمک میکنند. اگر یکی از این
معیارها به درستی رعایت نشوند، تکلیف ارائه شده مردود خواهد شد: اگر از ماژول هایی به جز مواردی که مشخصاً مجاز
شمرده شده اند استفاده کنید، یا اگر توابعی غیر از توابع مجاز را تغییر دهید.
پیاده سازی تابع shortest_path را کامل کنید به طوری که کوتاه ترین مسیر از فرد با شناسۀ source (مبدأ) تا فرد با
شناسۀ target (مقصد) را به شما بدهد.
  - با فرض اینکه از source تا target مسیری وجود دارد، تابع شما باید لیستی را بدهد که هر آیتم آن، جفت بعدی
عه (movie_id, person_id) در مسیر بین مبدأ تا مقصد باشد. هر جفت باید زوج مرتبی از دو متغیر باشد.
    - برای مثال، اگر مقدار برگشتی shortest_path [(1, 2), (3, 4)] باشد، بدین معنا خواهد بود که مبدأ در
فیلم 1 با فرد 2 بازی کرده است و فرد 2 در فیلم 3 با فرد 4 بازی کرده است و فرد 4 مقصد است.
  - اگر از مبدأ تا مقصد، چندین مسیر با کمترین طول وجود داشته باشد، آنگاه تابع شما می تواند هر کدام از آنها را به
عنوان خروجی برگرداند.
  - اگر هیچ مسیر ممکنی بین دو بازیگر وجود نداشته باشد، آنگاه تابع شما باید None برگرداند.
  - میتوانید تابع neighbors_for_person را فرابخوانید؛ این تابع، شناسۀ فرد را به عنوان ورودی دریافت میکند و
مجموعه ای از جفت های (movie_id, person_id) را بر میگرداند که شامل تمامی افرادی است که با آن شخص
خاص در یک فیلم بازی کرده اند. 

شما نباید هیچ چیزی غیر از تابع shortest_path را در این فایل تغییر دهید اما میتوانید توابع دیگری را بنویسید یا از سایر
ماژول های کتابخانه ی استاندارد پایتون استفاده کنید.


### راهنمایی
  - اگرچه در زمان تدریس برای پیاده سازی الگوریتم های جستجو، بعد از اینکه گره، frontier را ترک کرد، شرط
رسیدن به هدف بررسی میشود اما شما می توانید در هنگامی که گره ها به frontier اضافه می شوند، این بررسی
را انجام دهید و بدین ترتیب کارایی الگوریتم جستجوی خود را بهبود بخشید: اگر گرهِ هدفی را شناسایی کردید،
نیازی نیست آن را به frontier اضافه کنید؛ بلکه میتوانید بلافاصله راه حل به دست آمده را به عنوان خروجی تابع
برگردانید.
  - میتوانید نمونه کدهای موجود در درس را بردارید یا از آنها اقتباس کنید. فایلی به نام util.py را از قبل برایتان
آماده کرده ایم که حاوی پیاده ساز یهای درس برای Node ، StackFrontier و QueueFrontier ا ست. می توانید
از آ نها استفاده کنید (و در صورت تمایل، آ نها را تغییر دهید).

موفق باشید.
- ***last update: 2022 Dec 31***
- ***State: complete***
