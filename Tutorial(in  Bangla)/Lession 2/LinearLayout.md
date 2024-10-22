অ্যান্ড্রয়েড ডেভেলপমেন্টে **LinearLayout** একটি গুরুত্বপূর্ণ **ViewGroup**, যা তার চাইল্ড ভিউগুলোকে লিনিয়ার ফ্যাশনে সাজায়, অর্থাৎ একটির পর একটি, হয় উল্লম্বভাবে (vertical) অথবা অনুভূমিকভাবে (horizontal)।

### LinearLayout এর মূল বৈশিষ্ট্য:
- **android:orientation**: নির্ধারণ করে যে চাইল্ড ভিউগুলো উল্লম্বভাবে (vertical) নাকি অনুভূমিকভাবে (horizontal) সাজানো হবে।
- **android:gravity**: কন্টেইনারের ভিতরে চাইল্ড ভিউগুলো কীভাবে অবস্থান করবে তা নিয়ন্ত্রণ করে।
- **android:layout_weight**: এটি ব্যবহার করে চাইল্ড ভিউগুলোর মধ্যে স্পেস ভাগ করা যায়, যা স্পেসকে ডায়নামিকভাবে বণ্টন করতে সাহায্য করে।

### XML উদাহরণ: উল্লম্বভাবে ভিউ সাজানো

```xml
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <!-- TextView: একটি লেবেল প্রদর্শন করবে -->
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="আপনার নাম লিখুন"
        android:textSize="18sp"
        android:paddingBottom="8dp" />

    <!-- EditText: ব্যবহারকারীর ইনপুট নেওয়ার জন্য -->
    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="নাম"
        android:padding="8dp"
        android:background="@android:drawable/editbox_background" />

    <!-- Button: একটি অ্যাকশন ট্রিগার করার জন্য -->
    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="সাবমিট"
        android:padding="12dp"
        android:textColor="#FFFFFF"
        android:background="#6200EE"
        android:layout_marginTop="16dp" />
</LinearLayout>
```

### অনুভূমিকভাবে ভিউ সাজানো উদাহরণ:

```xml
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="horizontal"
    android:gravity="center"
    android:padding="16dp">

    <!-- Button: প্রথম বাটন -->
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="বাটন ১"
        android:layout_weight="1" />

    <!-- Button: দ্বিতীয় বাটন -->
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="বাটন ২"
        android:layout_weight="1" />

    <!-- Button: তৃতীয় বাটন -->
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="বাটন ৩"
        android:layout_weight="1" />
</LinearLayout>
```

এই উদাহরণে, তিনটি বাটনকে অনুভূমিকভাবে সাজানো হয়েছে এবং **`layout_weight`** ব্যবহার করে স্পেস সমানভাবে ভাগ করা হয়েছে।

### সংক্ষেপে:

- **LinearLayout** ব্যবহার করে ভিউগুলোকে সহজে একসাথে উল্লম্ব বা অনুভূমিকভাবে সাজানো যায়।
- **layout_weight** দিয়ে চাইল্ড ভিউগুলোর মধ্যে স্পেস ডায়নামিকভাবে ভাগ করা যায়। 
- এটা সাধারণত সহজ এবং দ্রুত ইউজার ইন্টারফেস তৈরি করতে ব্যবহৃত হয়।
