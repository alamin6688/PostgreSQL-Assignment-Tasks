1️⃣ PostgreSQL কী?
🟢 সংজ্ঞা
PostgreSQL হলো একটি শক্তিশালী, ফ্রি এবং ওপেন-সোর্স ডেটাবেস ম্যানেজমেন্ট সিস্টেম। এটিকে object-relational DBMS বলা হয় কারণ এটি traditional relational database এর পাশাপাশি advanced feature (যেমন: JSON, indexing, stored procedures) সাপোর্ট করে।

🧩 ব্যবহারের ক্ষেত্র
বড় অ্যাপ্লিকেশন

সরকারি ডেটা সংরক্ষণ

ব্যাঙ্কিং ও নিরাপত্তা সংক্রান্ত সিস্টেম

💡 উদাহরণ
একটি বন সংরক্ষণ অ্যাপে rangers, species, sightings ডেটা PostgreSQL ডেটাবেসে রাখা যায়।

2️⃣ PostgreSQL-এ Schema এর ভূমিকা
🟢 Schema কী?
একটি schema হলো ডেটাবেসের ভিতরে আলাদা logical section বা container, যেখানে টেবিল, ফাংশন, ভিউ ইত্যাদি রাখা হয়।

📦 কেন প্রয়োজন?
একাধিক ইউজার বা টিম একসাথে কাজ করতে পারে

ডেটা আলাদা করে রাখতে সুবিধা হয়

নামের সংঘর্ষ (name conflict) এড়ানো যায়

💡 উদাহরণ
sql
Copy
Edit
public.users     -- সাধারণ ইউজারদের টেবিল
admin.users      -- অ্যাডমিন ইউজারদের টেবিল
3️⃣ Primary Key ও Foreign Key কী?
🔑 Primary Key:
একটি টেবিলের এমন একটি কলাম যা প্রতিটি রেকর্ডকে ইউনিকভাবে চিহ্নিত করে

null হতে পারে না

🔗 Foreign Key:
এটি অন্য টেবিলের Primary Key-কে রেফারেন্স করে

এটি টেবিলগুলোর মধ্যে সম্পর্ক তৈরি করে

💡 উদাহরণ
sql
Copy
Edit
-- rangers টেবিল
ranger_id SERIAL PRIMARY KEY

-- sightings টেবিল
ranger_id INT REFERENCES rangers(ranger_id)
এখানে sightings.ranger_id হলো rangers টেবিলের সঙ্গে সম্পর্কিত Foreign Key।

4️⃣ VARCHAR vs CHAR
বৈশিষ্ট্য	VARCHAR(n)	CHAR(n)
দৈর্ঘ্য	পরিবর্তনযোগ্য	নির্দিষ্ট
স্পেস	শুধুমাত্র যতটুকু লাগে	অতিরিক্ত স্পেস দিয়ে পূরণ করা হয়
পারফরম্যান্স	ভালো	একটু ধীর হতে পারে

💡 উদাহরণ
sql
Copy
Edit
name VARCHAR(100)  -- "Alamin" → 6 characters
code CHAR(5)       -- "AB" → "AB   "
✅ সাধারণত VARCHAR বেশি ব্যবহার করা হয় কারণ এটি স্টোরেজে সাশ্রয়ী এবং ফ্লেক্সিবল।

5️⃣ WHERE ক্লজের কাজ
🎯 ভূমিকা
WHERE clause হল একটি ফিল্টার, যা SELECT, UPDATE, DELETE ইত্যাদি statement-এ শর্ত অনুযায়ী ডেটা বের করতে ব্যবহার করা হয়।

💡 উদাহরণ
sql
Copy
Edit
SELECT * FROM rangers
WHERE region = 'River Delta';
এখানে শুধু সেই রেঞ্জারদের তথ্য দেখাবে যারা River Delta এলাকায় কাজ করছে।

🛠️ উপকারিতা
ডেটা ফিল্টার করা যায়

নির্দিষ্ট তথ্য বিশ্লেষণে সাহায্য করে

performance উন্নত হয় কারণ অপ্রয়োজনীয় ডেটা বাদ পড়ে
