# RICH STORE Bangladesh — Android থেকে সেটআপ (বাংলায়)

## ১) আগে ওয়েবসাইট ফাইল নাও
ZIP ফাইলটি extract করো। এর ভেতরে `index.html` আছে। ফোনের file manager দিয়ে ফাইলটি খুলে/শেয়ার করে ব্রাউজারে প্রিভিউ করা যায়, তবে সবার জন্য ওয়েবসাইট চালু করতে hosting লাগবে।

## ২) ফ্রি হোস্টিং (শুধু ওয়েবসাইটের ডিজাইন)
সহজ পথ:
1. GitHub-এ অ্যাকাউন্ট তৈরি/লগইন করো।
2. নতুন public repository বানাও, যেমন `rich-store-bangladesh`.
3. `index.html` ফাইলটি repository-তে upload করো।
4. Repository → Settings → Pages → Deploy from a branch → `main` এবং `/ (root)` বেছে Save করো।
5. GitHub Pages যে URL দেবে সেটি দিয়ে ওয়েবসাইট দেখা যাবে।
6. `index.html`-এর sample price, product names, descriptions এবং watch icon-গুলো নিজের অনুমোদিত product photo দিয়ে বদলাবে।

## ৩) অর্ডার ও ইমেইল চালু করতে
এই ZIP-এর checkout form এখন demo; এটি এখনও অর্ডার সেভ বা ইমেইল পাঠায় না।
1. Supabase-এ free project তৈরি করো।
2. SQL Editor-এ `supabase/schema.sql` চালাও।
3. Supabase Edge Function তৈরি/ডেপ্লয় করতে Supabase CLI বা সমর্থিত web IDE লাগবে। শুধু ফোন দিয়ে করা সম্ভব হলেও সেটআপ কিছুটা কঠিন হতে পারে।
4. `supabase/functions/create-checkout/index.ts`-এর TODO অংশ বাস্তবভাবে পূরণ করতে হবে। এই ফাইলটি একা real payment চালু করে না।
5. অর্ডার ইমেইলের জন্য Resend বা অন্য email provider-এ account তৈরি করে API key server-side secret হিসেবে রাখো।
6. Email notification শুধুমাত্র backend থেকে পাঠাবে; email API key HTML/JavaScript-এ রেখো না।

## ৪) বাংলাদেশে অনলাইন পেমেন্ট
1. SSLCommerz বা অন্য সমর্থিত বাংলাদেশি payment gateway-তে merchant account-এর জন্য আবেদন করো।
2. তাদের বর্তমান KYC, ব্যবসার তথ্য, website policy ও approval requirements পূরণ করো।
3. sandbox/test credentials নাও।
4. server-side function-এ payment session তৈরি করো এবং gateway callback/IPN server-side verify করো।
5. payment verified না হওয়া পর্যন্ত অর্ডারকে `paid` দেখাবে না।
6. sandbox test সফল হলে provider-এর নিয়ম অনুযায়ী live credentials বসাও।

## ৫) লাইভ করার আগে
- সব দাম ও পণ্যের স্পেসিফিকেশন supplier থেকে যাচাই করো।
- আসল পণ্যের ছবি ব্যবহারের অনুমতি নিশ্চিত করো।
- Delivery, return/refund, privacy এবং contact পেজ যোগ করো।
- মোবাইল নম্বর, ঠিকানা, অর্ডার ডেটা নিরাপদে রাখো।
- কয়েকটি test order করে checkout, email এবং payment status যাচাই করো।

## জরুরি সতর্কতা
`index.html`-এ কখনো SSLCommerz secret key, Supabase service-role key বা email API key রাখবে না। এই starter-এ payment এখনো সক্রিয় নয়। Real payment নেওয়ার আগে backend integration ও gateway approval আবশ্যক।
