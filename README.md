
<h2>1️⃣ What is PostgreSQL?</h2>

<h3>🟢 Definition</h3>
<p><strong>PostgreSQL</strong> is a powerful, free, and open-source database management system. It is called an <em>object-relational DBMS</em> because it supports advanced features (such as JSON, indexing, stored procedures) alongside traditional relational databases.</p>

<h3>🧩 Use Cases</h3>
<ul>
  <li>Large applications</li>
  <li>Government data storage</li>
  <li>Banking and security-related systems</li>
</ul>

<h3>💡 Example</h3>
<p>In a wildlife conservation app, data like <code>rangers</code>, <code>species</code>, and <code>sightings</code> can be stored in a PostgreSQL database.</p>

<h2>2️⃣ Role of Schema in PostgreSQL</h2>

<h3>🟢 What is a Schema?</h3>
<p>A <strong>schema</strong> is a separate logical section or container inside the database where tables, functions, views, etc. are stored.</p>

<h3>📦 Why is it needed?</h3>
<ul>
  <li>Multiple users or teams can work together</li>
  <li>Data can be organized separately</li>
  <li>Prevents name conflicts</li>
</ul>

<h3>💡 Example</h3>
<pre><code>public.users     -- tables for general users
admin.users      -- tables for admin users
</code></pre>

<h2>3️⃣ What are Primary Key and Foreign Key?</h2>

<h3>🔑 Primary Key:</h3>
<ul>
  <li>A column in a table that uniquely identifies each record</li>
  <li>Cannot be null</li>
</ul>

<h3>🔗 Foreign Key:</h3>
<ul>
  <li>References the Primary Key of another table</li>
  <li>Creates relationships between tables</li>
</ul>

<h3>💡 Example</h3>
<pre><code>-- In the rangers table
ranger_id SERIAL PRIMARY KEY

-- In the sightings table
ranger_id INT REFERENCES rangers(ranger_id)
</code></pre>

<p>Here, <code>sightings.ranger_id</code> is a Foreign Key linked to the <code>rangers</code> table.</p>

<h2>4️⃣ VARCHAR vs CHAR</h2>

<table>
  <thead>
    <tr>
      <th>Feature</th>
      <th><code>VARCHAR(n)</code></th>
      <th><code>CHAR(n)</code></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Length</td>
      <td>Variable</td>
      <td>Fixed</td>
    </tr>
    <tr>
      <td>Space</td>
      <td>Only uses as much as needed</td>
      <td>Spaces are padded if shorter</td>
    </tr>
    <tr>
      <td>Performance</td>
      <td>Better</td>
      <td>Can be slower</td>
    </tr>
  </tbody>
</table>

<h3>💡 Example</h3>
<pre><code>name VARCHAR(100)  -- "Alamin" → 6 characters
code CHAR(5)       -- "AB" → "AB   "
</code></pre>

<p>✅ Generally, <code>VARCHAR</code> is preferred as it is storage-efficient and flexible.</p>

<h2>5️⃣ Purpose of WHERE Clause</h2>

<h3>🎯 Role</h3>
<p>The <strong>WHERE clause</strong> acts as a filter in <code>SELECT</code>, <code>UPDATE</code>, <code>DELETE</code>, etc., statements to retrieve data based on conditions.</p>

<h3>💡 Example</h3>
<pre><code>SELECT * FROM rangers
WHERE region = 'River Delta';
</code></pre>

<p>This query returns only the rangers who work in the <code>River Delta</code> region.</p>

<h3>🛠️ Benefits</h3>
<ul>
  <li>Filters data</li>
  <li>Helps analyze specific information</li>
  <li>Improves performance by excluding unnecessary data</li>
</ul>

<hr>


