<h1>🎓 Bonus Section – বাংলা উত্তর</h1>

<p>এই অংশে ৫টি বোনাস প্রশ্নের উত্তর দেওয়া হলো। প্রতিটি উত্তর উদাহরণসহ ব্যাখ্যা করা হয়েছে যাতে PostgreSQL-এর ধারণা স্পষ্টভাবে বোঝা যায়।</p>

<h2>1️⃣ PostgreSQL কী?</h2>

<h3>🟢 সংজ্ঞা</h3>
<p><strong>PostgreSQL</strong> হলো একটি শক্তিশালী, ফ্রি এবং ওপেন-সোর্স ডেটাবেস ম্যানেজমেন্ট সিস্টেম। এটিকে <em>object-relational DBMS</em> বলা হয় কারণ এটি traditional relational database এর পাশাপাশি advanced feature (যেমন: JSON, indexing, stored procedures) সাপোর্ট করে।</p>

<h3>🧩 ব্যবহারের ক্ষেত্র</h3>
<ul>
  <li>বড় অ্যাপ্লিকেশন</li>
  <li>সরকারি ডেটা সংরক্ষণ</li>
  <li>ব্যাঙ্কিং ও নিরাপত্তা সংক্রান্ত সিস্টেম</li>
</ul>

<h3>💡 উদাহরণ</h3>
<p>একটি বন সংরক্ষণ অ্যাপে <code>rangers</code>, <code>species</code>, <code>sightings</code> ডেটা PostgreSQL ডেটাবেসে রাখা যায়।</p>

<h2>2️⃣ PostgreSQL-এ Schema এর ভূমিকা</h2>

<h3>🟢 Schema কী?</h3>
<p>একটি <strong>schema</strong> হলো ডেটাবেসের ভিতরে আলাদা logical section বা container, যেখানে টেবিল, ফাংশন, ভিউ ইত্যাদি রাখা হয়।</p>

<h3>📦 কেন প্রয়োজন?</h3>
<ul>
  <li>একাধিক ইউজার বা টিম একসাথে কাজ করতে পারে</li>
  <li>ডেটা আলাদা করে রাখতে সুবিধা হয়</li>
  <li>নামের সংঘর্ষ (name conflict) এড়ানো যায়</li>
</ul>

<h3>💡 উদাহরণ</h3>
<pre><code>public.users     -- সাধারণ ইউজারদের টেবিল
admin.users      -- অ্যাডমিন ইউজারদের টেবিল
</code></pre>

<h2>3️⃣ Primary Key ও Foreign Key কী?</h2>

<h3>🔑 Primary Key:</h3>
<ul>
  <li>একটি টেবিলের এমন একটি কলাম যা প্রতিটি রেকর্ডকে ইউনিকভাবে চিহ্নিত করে</li>
  <li>null হতে পারে না</li>
</ul>

<h3>🔗 Foreign Key:</h3>
<ul>
  <li>এটি অন্য টেবিলের Primary Key-কে রেফারেন্স করে</li>
  <li>টেবিলগুলোর মধ্যে সম্পর্ক তৈরি করে</li>
</ul>

<h3>💡 উদাহরণ</h3>
<pre><code>-- rangers টেবিল
ranger_id SERIAL PRIMARY KEY

-- sightings টেবিল
ranger_id INT REFERENCES rangers(ranger_id)
</code></pre>

<p>এখানে <code>sightings.ranger_id</code> হলো <code>rangers</code> টেবিলের সঙ্গে সম্পর্কিত Foreign Key।</p>

<h2>4️⃣ VARCHAR vs CHAR</h2>

<table>
  <thead>
    <tr>
      <th>বৈশিষ্ট্য</th>
      <th><code>VARCHAR(n)</code></th>
      <th><code>CHAR(n)</code></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>দৈর্ঘ্য</td>
      <td>পরিবর্তনযোগ্য</td>
      <td>নির্দিষ্ট</td>
    </tr>
    <tr>
      <td>স্পেস</td>
      <td>শুধুমাত্র যতটুকু লাগে</td>
      <td>অতিরিক্ত স্পেস দিয়ে পূরণ করা হয়</td>
    </tr>
    <tr>
      <td>পারফরম্যান্স</td>
      <td>ভালো</td>
      <td>একটু ধীর হতে পারে</td>
    </tr>
  </tbody>
</table>

<h3>💡 উদাহরণ</h3>
<pre><code>name VARCHAR(100)  -- "Alamin" → 6 characters
code CHAR(5)       -- "AB" → "AB   "
</code></pre>

<p>✅ সাধারণত <code>VARCHAR</code> বেশি ব্যবহার করা হয় কারণ এটি স্টোরেজে সাশ্রয়ী এবং ফ্লেক্সিবল।</p>

<h2>5️⃣ WHERE ক্লজের কাজ</h2>

<h3>🎯 ভূমিকা</h3>
<p><strong>WHERE clause</strong> হল একটি ফিল্টার, যা <code>SELECT</code>, <code>UPDATE</code>, <code>DELETE</code> ইত্যাদি statement-এ শর্ত অনুযায়ী ডেটা বের করতে ব্যবহার করা হয়।</p>

<h3>💡 উদাহরণ</h3>
<pre><code>SELECT * FROM rangers
WHERE region = 'River Delta';
</code></pre>

<p>এখানে শুধু সেই রেঞ্জারদের তথ্য দেখাবে যারা <code>River Delta</code> এলাকায় কাজ করছে।</p>

<h3>🛠️ উপকারিতা</h3>
<ul>
  <li>ডেটা ফিল্টার করা যায়</li>
  <li>নির্দিষ্ট তথ্য বিশ্লেষণে সাহায্য করে</li>
  <li>performance উন্নত হয় কারণ অপ্রয়োজনীয় ডেটা বাদ পড়ে</li>
</ul>

<hr>

