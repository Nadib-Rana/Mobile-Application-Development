**TableLayout** হলো একটি ভিউ গ্রুপ যা ভিউগুলিকে টেবিল ফরম্যাটে সাজায়। এটি **Rows** এবং **Columns** এ ভিউগুলিকে সাজানোর জন্য ব্যবহৃত হয়, যেখানে প্রতিটি রোতে একাধিক সেল বা কলাম থাকতে পারে। **TableLayout** এর ভিউগুলো **TableRow** তে সজ্জিত করা হয় এবং প্রতিটি **TableRow** এর মধ্যে চাইল্ড ভিউ থাকে, যা টেবিলের সেলগুলোর মত কাজ করে।

### TableLayout এর প্রধান বৈশিষ্ট্যসমূহ:
- **TableRow**: এটি একটি টেবিলের রো হিসেবে কাজ করে এবং প্রতিটি রোতে একাধিক ভিউ (যেমন টেক্সট ভিউ, বাটন ইত্যাদি) রাখা যায়।
- **Stretch Columns**: আপনি টেবিলের একটি নির্দিষ্ট কলামকে প্রসারিত করতে চাইলে এটি ব্যবহার করতে পারেন।
- **Shrink Columns**: একটি নির্দিষ্ট কলামকে সংকুচিত করার জন্য ব্যবহৃত হয়।
- **Collapse Columns**: এটি একটি নির্দিষ্ট কলামকে সম্পূর্ণরূপে লুকিয়ে দেয়।

### TableLayout এর উদাহরণ:
নিচে একটি সাধারণ **TableLayout** এর উদাহরণ দেওয়া হলো যেখানে তিনটি রো রয়েছে এবং প্রতিটি রোতে ভিন্ন ভিন্ন সংখ্যক সেল রয়েছে:

```xml
<TableLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:stretchColumns="1">

    <!-- প্রথম রো -->
    <TableRow>
        <TextView
            android:text="Name"
            android:padding="10dp"
            android:textStyle="bold" />
        <TextView
            android:text="John Doe"
            android:padding="10dp" />
    </TableRow>

    <!-- দ্বিতীয় রো -->
    <TableRow>
        <TextView
            android:text="Age"
            android:padding="10dp"
            android:textStyle="bold" />
        <TextView
            android:text="25"
            android:padding="10dp" />
    </TableRow>

    <!-- তৃতীয় রো -->
    <TableRow>
        <TextView
            android:text="Occupation"
            android:padding="10dp"
            android:textStyle="bold" />
        <TextView
            android:text="Software Developer"
            android:padding="10dp" />
    </TableRow>
</TableLayout>
```

#### ব্যাখ্যা:
1. **TableLayout** এর মধ্যে তিনটি **TableRow** রয়েছে, যেখানে প্রতিটি রোতে দুটি করে কলাম আছে।
2. প্রথম কলামে লেবেল (যেমন, **Name**, **Age**, **Occupation**) এবং দ্বিতীয় কলামে তাদের মান (যেমন, **John Doe**, **25**, **Software Developer**) আছে।
3. `android:stretchColumns="1"` দ্বারা দ্বিতীয় কলামটি প্রসারিত হয়েছে, যাতে এটি পুরো প্রস্থ দখল করে।

### colspan এবং rowspan-এর মতো বৈশিষ্ট্য:
**TableLayout** এ সরাসরি **colspan** এবং **rowspan** সমর্থিত নয়। তবে আপনি এই ধরনের কার্যকারিতা অর্জনের জন্য ভিন্ন ভিন্ন **TableRow** এ ভিউগুলো রাখার মাধ্যমে কাজ করতে পারেন। উদাহরণস্বরূপ, একটি ভিউকে পুরো রো জুড়ে রাখতে চাইলে, আপনি শুধু সেই ভিউকে একটি **TableRow** এ রাখবেন।

#### colspan এর মতো উদাহরণ:
```xml
<TableLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content">

    <!-- প্রথম রো -->
    <TableRow>
        <TextView
            android:text="Name"
            android:padding="10dp"
            android:textStyle="bold" />
        <TextView
            android:text="John Doe"
            android:padding="10dp" />
    </TableRow>

    <!-- দ্বিতীয় রো, যেখানে colspan এর মতো কাজ হচ্ছে -->
    <TableRow>
        <TextView
            android:text="Single cell spanning both columns"
            android:padding="10dp"
            android:layout_span="2"
            android:gravity="center" />
    </TableRow>
</TableLayout>
```

#### ব্যাখ্যা:
- **layout_span="2"** ব্যবহার করা হয়েছে যাতে দ্বিতীয় রোতে একটি টেক্সট ভিউ দুটি কলামের উপর জায়গা নেয়, এটি কার্যত **colspan** এর মতো কাজ করে।

### Important Properties of TableLayout:
1. **android:stretchColumns**: টেবিলের একটি বা একাধিক কলাম প্রসারিত করতে ব্যবহার করা হয়। এটি প্রসারিত হওয়ার জন্য কোন কোন কলাম নির্বাচন করা হবে তা ইনডেক্স দ্বারা নির্ধারণ করতে হবে।
2. **android:shrinkColumns**: টেবিলের একটি বা একাধিক কলাম সংকুচিত করতে ব্যবহার করা হয়।
3. **android:collapseColumns**: কোন কলামকে সম্পূর্ণরূপে লুকিয়ে রাখতে ব্যবহার করা হয়।

### Complex TableLayout Example:
```xml
<TableLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:stretchColumns="1,2">

    <!-- প্রথম রো -->
    <TableRow>
        <TextView
            android:text="Name"
            android:padding="10dp" />
        <TextView
            android:text="Age"
            android:padding="10dp" />
        <TextView
            android:text="Occupation"
            android:padding="10dp" />
    </TableRow>

    <!-- দ্বিতীয় রো -->
    <TableRow>
        <TextView
            android:text="John Doe"
            android:padding="10dp" />
        <TextView
            android:text="25"
            android:padding="10dp" />
        <TextView
            android:text="Software Developer"
            android:padding="10dp" />
    </TableRow>

    <!-- তৃতীয় রো -->
    <TableRow>
        <TextView
            android:text="Jane Smith"
            android:padding="10dp" />
        <TextView
            android:text="30"
            android:padding="10dp" />
        <TextView
            android:text="Graphic Designer"
            android:padding="10dp" />
    </TableRow>
</TableLayout>
```
### উপসংহার:
- **TableLayout** হল একটি লেআউট যা আপনাকে রো এবং কলামের ফরম্যাটে ভিউ সাজাতে সাহায্য করে, টেবিলের মতো।
- এটি সহজে টেবিলভিত্তিক লেআউট তৈরি করতে দেয় এবং **stretchColumns**, **shrinkColumns**, এবং **layout_span** এর মতো বৈশিষ্ট্য ব্যবহার করে ভিউগুলোর সাইজ নিয়ন্ত্রণ করা যায়।
- জটিল লেআউট তৈরি করার জন্য **TableLayout** বেশ কার্যকর, তবে টেবিলের নেস্টিং এড়ানো উচিত কারণ এটি পারফরম্যান্সে প্রভাব ফেলতে পারে।
