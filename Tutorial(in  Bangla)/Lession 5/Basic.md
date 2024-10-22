### ১. **What is an Activity?**
**Activity** হলো Android অ্যাপ্লিকেশনের একটি প্রধান উপাদান, যা সাধারণত একটি একক স্ক্রিন বা ইউজার ইন্টারফেস উপস্থাপন করে। ব্যবহারকারীর সাথে সরাসরি ইন্টারঅ্যাক্ট করে এমন UI উপাদানগুলো **Activity** তে থাকে। প্রতিটি **Activity** একটি অ্যাপের নির্দিষ্ট কার্যকলাপ সম্পন্ন করে, যেমন একটি লিস্ট দেখানো বা ফর্ম পূরণ করা। একটি Android অ্যাপ একাধিক **Activity** নিয়ে গঠিত হতে পারে, এবং একটি অ্যাপ চালু হওয়ার পর একটি **Activity** প্রথমে প্রদর্শিত হয়।

### ২. **Declaration of Activities in Manifest File**
প্রতিটি **Activity** কে **AndroidManifest.xml** ফাইলে ঘোষণা করতে হয়, কারণ এটি অ্যাপ্লিকেশনের কাঠামো এবং বৈশিষ্ট্য সম্পর্কে সিস্টেমকে তথ্য দেয়। **AndroidManifest.xml** এ **Activity** ঘোষণা করার উদাহরণ নিচে দেওয়া হলো:


```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.myapp">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">

        <!-- Activity declaration -->
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        
        <activity android:name=".SecondActivity" />

    </application>
</manifest>
```

#### ব্যাখ্যা:
- **MainActivity** হলো অ্যাপ্লিকেশনের প্রধান **Activity**, যা অ্যাপ চালু হলে প্রথম প্রদর্শিত হয়।
- **intent-filter** দিয়ে **MainActivity** কে লঞ্চার **Activity** হিসেবে নির্ধারণ করা হয়েছে।
- **SecondActivity** একটি সাধারণ **Activity** হিসেবে ঘোষণা করা হয়েছে।

### ৩. **Activities and Application**
একটি **Android Application** বিভিন্ন **Activities** নিয়ে গঠিত, এবং প্রতিটি **Activity** একটি নির্দিষ্ট কাজের জন্য দায়ী। একটি **Activity** একটি **UI** নিয়ে কাজ করে এবং একাধিক **Activity** এর মাধ্যমে ব্যবহারকারীর সাথে ইন্টারঅ্যাক্ট করে। একে একে বিভিন্ন **Activity** এর মধ্যে নেভিগেট করার মাধ্যমে অ্যাপ্লিকেশনটি কাজ সম্পন্ন করে। প্রতিটি **Activity** এর নিজস্ব ইন্ডিপেন্ডেন্ট UI থাকে এবং অ্যাপের ভিন্ন ভিন্ন অংশ উপস্থাপন করে।

- **Example**: একটি ই-কমার্স অ্যাপ এ ব্যবহারকারী **LoginActivity** থেকে লগইন করে, এরপর **ProductListActivity** তে চলে যায় যেখানে পণ্যগুলো দেখা যায় এবং অবশেষে **CheckoutActivity** তে চেকআউট করা হয়।

### ৪. **Activity Life-cycle**
একটি **Activity** এর লাইফ-সাইকেল বিভিন্ন পর্যায়ের মাধ্যমে পরিচালিত হয়, এবং Android সিস্টেম প্রতিটি পর্যায়ে নির্দিষ্ট মেথড কল করে। **Activity** এর লাইফ-সাইকেল মূলত ব্যবহারকারীর ইন্টারঅ্যাকশন এবং অ্যাপ্লিকেশনের অবস্থা (যেমন ব্যাকগ্রাউন্ডে যাওয়া বা বন্ধ হওয়া) অনুযায়ী কাজ করে।

#### Activity Life-cycle এর প্রধান মেথড:
1. **onCreate()**: Activity প্রথমবার শুরু হলে কল হয়, এখানে আপনি UI তৈরি করেন এবং প্রাথমিক সেটআপ করেন।
2. **onStart()**: Activity দৃশ্যমান হলে এই মেথডটি কল হয়।
3. **onResume()**: Activity ব্যবহারকারীর সাথে ইন্টারঅ্যাক্ট করতে প্রস্তুত হলে এটি কল হয়।
4. **onPause()**: Activity ব্যাকগ্রাউন্ডে চলে গেলে এটি কল হয়।
5. **onStop()**: Activity সম্পূর্ণ দৃশ্যমান না থাকলে কল হয়।
6. **onDestroy()**: Activity বন্ধ হওয়ার আগে এটি কল হয়।

#### Life-cycle Diagram:

- **onCreate() → onStart() → onResume()** → Activity চলছে
- **onPause()** → Activity অস্থায়ীভাবে বন্ধ
- **onStop()** → Activity ব্যাকগ্রাউন্ডে
- **onDestroy()** → Activity সম্পূর্ণরূপে ধ্বংস হয়ে গেছে

### ৫. **Activity Stack (Back Stack)**
**Activity Stack**, যাকে **Back Stack** ও বলা হয়, Android সিস্টেমে **Activities** কিভাবে পরিচালিত হয় তা বোঝায়। Android একটি স্ট্যাকের মতো পদ্ধতিতে **Activities** পরিচালনা করে, যেখানে নতুন **Activity** শুরু হলে এটি স্ট্যাকের শীর্ষে যোগ হয় এবং আগের **Activity** ব্যাকগ্রাউন্ডে চলে যায়। ব্যবহারকারী যখন **Back** বাটন চাপেন, তখন স্ট্যাকের শীর্ষে থাকা **Activity** সরিয়ে ফেলা হয় এবং আগের **Activity** সামনে আসে।

#### উদাহরণ:
1. **MainActivity** শুরু হয় → স্ট্যাক: [MainActivity]
2. **SecondActivity** শুরু হয় → স্ট্যাক: [MainActivity, SecondActivity]
3. **ThirdActivity** শুরু হয় → স্ট্যাক: [MainActivity, SecondActivity, ThirdActivity]
4. ব্যবহারকারী **Back** বাটন চাপলে **ThirdActivity** বন্ধ হয় এবং **SecondActivity** সামনে আসে → স্ট্যাক: [MainActivity, SecondActivity]

#### Activity Stack Behavior:
- **SingleTask**: একটি অ্যাপ্লিকেশন একই **Activity** কে একাধিকবার স্ট্যাকের মধ্যে রাখে না, এটি স্ট্যাকের আগে থেকেই উপস্থিত হলে সরাসরি পুনরায় ব্যবহার করে।
- **SingleTop**: যদি স্ট্যাকের শীর্ষে ইতিমধ্যে একই **Activity** থাকে, তবে এটি পুনরায় তৈরি হয় না।
  
### উপসংহার:
- **Activity** হলো Android অ্যাপ্লিকেশনের একটি প্রধান উপাদান, যা UI এবং ব্যবহারকারীর সাথে ইন্টারঅ্যাকশন পরিচালনা করে।
- **Activity Life-cycle** এর মেথডগুলো Activity এর বিভিন্ন অবস্থা নিয়ন্ত্রণ করে।
- **Activity Stack** ব্যাক বাটনের মাধ্যমে ব্যবহারকারীর নেভিগেশনকে পরিচালনা করে।
