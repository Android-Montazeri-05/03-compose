
# جزوه آموزشی: مقدمه برنامه‌نویسی موبایل با کاتلین و Jetpack Compose

## ۱. مقدمه و آشنایی با مفاهیم پایه

کاتلین (**Kotlin**) زبان برنامه‌نویسی رسمی و مدرن توسعه اندروید است که توسط شرکت JetBrains توسعه داده شده است. ویژگی‌های برجسته‌ای نظیر ایمنی در برابر خطاهای رایج (به‌ویژه Null Safety)، سادگی، خوانایی بالا و سازگاری کامل با جاوا، آن را به انتخاب اول توسعه‌دهندگان تبدیل کرده است.

در کنار کاتلین، **Jetpack Compose** جعبه‌ابزار مدرن گوگل برای ساخت رابط کاربری (UI) بومی در اندروید به شمار می‌رود. این فریمورک از الگوی **اعلامی (Declarative)** بهره می‌برد؛ بدین معنا که به جای دستکاری مستقیم درخت ویوها یا نوشتن کدهای طولانی XML، رابط کاربری با توابع کاتلین توصیف می‌شود که فرآیند طراحی را خواناتر، کوتاه‌تر و سریع‌تر می‌کند.

---

## ۲. ساختار پروژه اندروید

در معماری پروژه‌های استاندارد بر پایه Compose، سازمان‌دهی فایل‌ها به شکل زیر است:

* **پوشه کدهای برنامه (`src/main/kotlin` یا `src/main/java`):** محل قرارگیری کلاس‌ها، معماری اپلیکیشن و توابع رابط کاربری.
* **پوشه منابع (`res`):** نگهداری فایل‌های غیرکدی شامل تصاویر، آیکون‌ها، رشته‌های متنی (Strings) و تم رنگی پروژه.
* **اسکریپت‌های ساخت (`build.gradle`):** تعریف وابستگی‌ها (Dependencies)، متغیرهای ساخت، تنظیمات کامپایلر و نسخه‌های SDK.

---

## ۳. اجزای اصلی رابط کاربری در Jetpack Compose

رابط کاربری در کامپوز با چینش و ترکیب توابع نشانه‌گذاری‌شده با `@Composable` شکل می‌گیرد. پرکاربردترین کامپوننت‌های پایه به شرح زیر هستند:

### الف) کامپوننت متن (`Text`)

برای نمایش متن و تعیین ویژگی‌های تایپوگرافی مانند اندازه، فونت و رنگ استفاده می‌شود:

```kotlin
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.unit.sp

@Composable
fun GreetingText() {
    Text(
        text = "سلام، خوش آمدید!",
        fontSize = 24.sp,
        color = Color.Blue
    )
}

```

---

### ب) کامپوننت دکمه (`Button`)

ابزاری برای دریافت اکشن و کلیک کاربر و اجرای لاجیک مشخص:

```kotlin
import androidx.compose.material3.Button
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable

@Composable
fun SimpleButton() {
    Button(
        onClick = {
            // اکشن مورد نظر هنگام کلیک روی دکمه
            println("دکمه فشرده شد!")
        }
    ) {
        Text(text = "ورود به حساب")
    }
}

```

---

### ج) چیدمان‌ها (`Column` و `Row`)

برای ساختارهای چیدمانی المان‌ها:

* **`Column`:** چینش عمودی عناصر (از بالا به پایین).
* **`Row`:** چینش افقی عناصر (از چپ به راست / راست به چپ بر اساس جهت زبان).

```kotlin
import androidx.compose.foundation.layout.Column
import androidx.compose.foundation.layout.Row
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable

@Composable
fun ProfileLayout() {
    Column {
        Text(text = "نام کاربری: علی")
        
        Row {
            Text(text = "وضعیت: ")
            Text(text = "آنلاین")
        }
    }
}

```

---

### د) اصلاح‌گر (`Modifier`)

مودیفایرها برای سفارشی‌سازی ظاهر، ابعاد، استایل و رفتار یک کامپوننت (مانند حاشیه، فاصله‌گذاری، پس‌زمینه و رویدادهای لمسی) به کار می‌روند:

```kotlin
import androidx.compose.foundation.background
import androidx.compose.foundation.layout.Box
import androidx.compose.foundation.layout.padding
import androidx.compose.foundation.layout.size
import androidx.compose.runtime.Composable
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.unit.dp

@Composable
fun BoxExample() {
    Box(
        modifier = Modifier
            .size(100.dp)          // ابعاد عرض و ارتفاع
            .background(Color.Red) // رنگ پس‌زمینه
            .padding(16.dp)        // فاصله درونی (Padding)
    )
}

```
