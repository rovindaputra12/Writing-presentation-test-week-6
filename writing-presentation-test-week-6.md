 # **Writing and Presentation Test Week 6** #
## **DATABASE MYSQL BASIC**
### **Database Introduction**
Database adalah kumpulan informasi yang disimpan didalam komputer secara sistematik dan saling berelasi.
Database merupakan sekumpulan tabel yang berisikan informasi untuk diolah yang kemudian data tersebut bisa digunakan di dalam sebuah sistem.

Untuk membuat Database diperlukan sebuah software yang dinamakan dengan DBMS(Database Management System)

### **Database Management System**
DBMS adalah software yang dapat digunakan oleh user untuk berkomunikasi dengan data yang ada dalam media penyimpanan.
### **Istilah pada Database**
- **Table**
    <div align="justify">Table adalah kumpulan value yang dibangun oleh baris dan kolom, yang didalamnya berisikan atribut dari sebuah data.
- **Field**
    <div align="justify">Field adalah kolom dari sebuah tabel dimana masing-masing field memiliki tipe data masing-masing.
- **Record**
    <div align="justify">Record merupakan kumpulan nilai yang saling terkait. Record merupakan isi dari sebuah tabel.

- **SQL**
    <div align="justify">SQL atau Structured Query Language merupakan suatu bahasa (Language) yang digunakan untuk mengakses database.

    SQL adalah Bahasa Query yang digunakan untuk melakukan interaksi di RDMS (Relational Database Management System).
    - Membuat, Menampilkan dan menghapus data didalam database
    - Mengatur “Permission” (siapa saja yang bisa mengakses data
    - Membuat dan menghapus Database.

- **DDL (Data Definition Language)**
    <div align="justify">DDL merupakan kumpulan perintah SQL yang digunakan untuk membuat, mengubah dan menghapus struktur dan definisi metadata dari objek-objek Database.

    ```
    Contoh perintah membuat tabel mahasiswa

    create table mahasiswa(
        kode_mahasiswa varchar(10) auto_increment,
        nama varchar(50),
        jurusan varchar(50),
        primary key(nim)
    );
    ```

- **ALTER**
    <div align="justify">Alter digunakan untuk mengubah struktur dari tabel yang ada, seperti untuk menambahkan atau menghapus kolom/field.
    Membuat atau menghapus primary key, mengubah jenis kolom/field yang ada, juga mengubah kolom atau nama tabel.

    ```
    Menambah Primary Key

    ALTER TABLE nama_tabel ADD Primary key (nama field) ALTER TABLE pasien ADD PRIMARY KEY (KdPasien)

    Menambah Kolom/Field

    ALTER TABLE nama_tabel ADD Nama_Field Tipe_Data(Ukuran) ALTER TABLE table pasien ADD Alamat Pasien varchar(50)

    Mengubah struktur tabel untuk field Alamat Pasien dari Length (50) menjadi (40) ALTER TABLE pasien ALTER COLUMN Alamat Pasien varchar(40)
    ```
- **DROP**
     <div align="justify">Perintah Drop digunakan untuk menghapus Database, Table, dan View atau Index.
     
     ```
     DROP DATABASE nama-databas
     ```

### **DML (Data Manipulation Language)**
- **SELECT**
    <div align="justify">Perintah SELECT digunakan untuk menyeleksi data berdasarkan syarat yang diberikan.

    Dengan menggunakan perintah SELECT ini record didalam tabel tertentu yang berjumlah ribuan bahkan jutaan dapat ditampilkan.

    ```
    SELECT COLUMN_NAME FROM TABLE_NAME

    SELECT DISTINCT COLUMN_NAME FROM TABLE_NAME
    ```
- **INSERT**
    <div align="justify">INSERT	digunakan untuk memasukkan data ke kolom-kolom yang terdapat pada tabel/vie.

    ```
    INSERT INTO NAMA_TABLE (nama_field1, nama field2, ...nama_fieldN) VALUES (valuel, value2,...., valueN)
    ```
- **Where, And, Or, Not, Like**
    ```
    SELECT column1, colum2

    FROM table_name

    WHERE condition1 AND condition2 OR condition3 NOT condition;
    ```
- **UPDATE**
    <div align="justify">Digunakan untuk melakukan editing pada isi dari kolom (field) yang dipilih. Hal ini dilakukan untuk memperbaiki data lama / terjadi kesalahan.

    ```
    UPDATE table_name SET column_name ="new data" WHERE key_column = 1;
    ```
- **DELETE**
    <div align="justify">Digunakan untuk menghapus data dalam tabel yang menjadi target.

    ```
    DELETE FROM table_name WHERE condition;
    ```
### **Database Relationships**
Database relationship adalah relasi atau hubungan antara beberapa tabel dalam bahasa yang kita miliki.

Relasi antar tabel dihubungkan oleh Primary key dan foreign key.
- Primary key adalah atribut yang tidak hanya mengidentifikasi secara unik suatu kejadian, tapi juga mewakili setiap kejadian suatu entitas.

    ```
    create table mahasiswa(
        nim int primary key auto_increment,
        nama varchar(50),
        jurusan varchar(50),
    );

    nim pada tabel mahasiswa di jadikan primary key
    ```
- Foreign key adalah atribut yang melengkapi relationship dan menunjukan hubungan antara tabel induk dengan tabel anak.
    ```
    create table fav_movie(
        id_favMovie int primary key auto_increment,
        id_mahasiswa int,
        FOREIGN KEY (id_mahasiswa) REFERENCES mahasiswa(nim)
    );
    ```

### **Beberapa tipe database relationships:**
- One To One Relationships
- One to Many and Many to One Relationships
- Many to Many Relationships
- Self Referencing Relationships

Contoh kasus :
- One To One Relationships : 
    <div align="justify">Tabel mahasiswa dan tabel alamat yakni 1 mahasiswa hanya memiliki 1 alamat begitu pula sebaliknya 1 alamat ahnya di miliki 1 mahasiswa.
-  One to Many and Many to One Relationships :
    <div align="justify"> tabel Customers dan tabel order barang. yakni 1 customer dapat memiliki banyak order barang.
- Many to Many Relationships :
    tabel order dan tabel item yakni 1 order dapat memiliki banyak item begitu sebaliknya 1 item memiliki banyak order.



## **DATABASE MYSQL LANJUTAN**
### **SQL Table Join**
Join, adalah penggabungan tabel yang dilakukan melalui kolom/key tertentu yang memiliki nilai terkait untuk mendapatkan satu set data dengan informasi lengkap.
<br>

- Inner Join : menampilkan data hanya yang sesuai di kedua tabel.
    ```
    SELECT * FROM karyawan INNER JOIN gaji ON karyawan.karyawan_id = gaji.karyawan_id;
    ```
- Left Join : menampilkan semua data sebelah kiri dari tabel yang di joinkan dan menampilkan data sebelah kanan yang cocok dengan kondisi join. Jika tidak ditemukan kecocokan, maka akan di set NULL secara otomatis

    ```
    SELECT * FROM karyawan LEFT JOIN gaji ON karyawan.karyawan_id = gaji.karyawan_id;
    ```
- Right Join : menampilkan semua data sebelah kanan dari tabel yang di joinkan dan menampilkan data sebelah kiri yang cocok dengan kondisi join. Jika tidak ditemukan kecocokan, maka akan di set NULL secara otomatis.

    ```
    SELECT * FROM gaji RIGHT JOIN karyawan ON gaji.karyawan_id = karyawan.karyawan_id;
    ```

### **NoSQL**
Database NoSQL adalah database yang tidak memiliki perintah SQL.

Konsep penyimpanannya semi struktural atau tidak struktural, dan tidak harus memiliki relasi layaknya tabel-tabel MySQL.

Tujuan dari penggunaan database noSQL adalah untuk model data spesifik dan memiliki skema fleksibel dalam mengembangkan aplikasi modern, contoh: aplikasi yang bersifat real time.

### **Kelebihan NoSQL di banding Relasional Database.**
- NoSQL bisa menampung data yang terstruktur, semi terstruktur dan tidak terstruktur.
- Menggunakan OOP dalam pengaksesan/manipulasi data.
- NoSQL tidak mengenal schema tabel yang kaku.
### **Document Database**
Document adalah salah satu dari beberapa model database NoSQL.

Mendefinisikan database sebagai dokumen artinya penyimpan data dan proses manipulasinya dalam bentuk Objek dokumen.
- Contoh objek dokumen yang sering diterapkan dalam pemrograman adalah format JSON.

### **Database Normalization**
- **Pengertian Database Normalization**
    <div align="justify">Merupakan teknik analisis data yang mengorganisasikan atribut-atribut data dengan cara mengelompokkan sehingga terbentuk entitas yang non-redundant, stabil, dan fleksible.
- **Tujuan Database Normalization**
    <div align="justify">Menghilangkan redundan data pada database.
    Memudahkan juka ada perubahan struktur table database.
    Memperkecil pengaruh jika ada perubahan dari struktur table database.
- **Efek Jika Tidak Melakukan Database Normalization**
    - INSERT Anomali : Situasi dimana tidak memungkinkan memasukkan beberapa jenis data secara langsung di database.


    - DELETE Anomali : Penghapusan data yang tidak sesuai dengan yang diharapkan, artinya data yang harusnya tidak terhapus mungkin ikut terhapus.


    - UPDATE Anomali : Situasi dimana nilai yang diubah menyebabkan inkonsistensi database, dalam artian data yang diubah tidak sesuai dengan yang diperintahkan atau yang diinginkan.
 - **Bentuk Database Normalization**
    **First Normal Form (1NF)**
    - Menghilangkan multiple value pada sebuah kolom table database
    - Sebuah table memenuhi kaidah 1NF jika :
        - Setiap kolom bernilai tunggal (single value)
        - Setiap kolom memiliki nama yang unik
        - Urutan penyimpanan data tidak menjadi masalah

- **Second Normal Form (2NF)**
    - Harus sudah dalam bentuk 1NF untuk mendapatkan 2NF
    - Menghapus beberapa subset data yang ada pada tabel dan menempatkan mereka pada tabel terpisah.
- **Third Normal Form (3NF)**
    - Menghilangkan seluruh atribut atau field yang tidak berhubungan dengan primary key. Dengan demikian tidak ada ketergantungan transitif pada setiap kandidat key.

### **Keys di SQL**
- **Super Key**
    - Kumpulan dari satu atau lebih dari satu key yang dapat digunakan untuk mengidentifikasi record secara unik dalam sebuah tabel
    - Super Key adalah superset dari Candidate Key.

- **Candidate Key**
    - kumpulan satu atau lebih fields/columns yang dapat mengidentifikasi record secara unik dalam tabel.
    - Bisa jadi ada beberapa Candidate Keys di dalam satu tabel
    - Setiap Candidate Key bisa digunakan sebagai Primary Key.
    - Candidate Key adalah super key yang tidak mempunyai value yang berulang

- **Primary Key**
    - kumpulan satu atau lebih fields/columns dari sebuah tabel yang secara unik mengidentifikasi sebuah record dalam tabel database.
    - Valuenya tidak boleh berupa null ataupun duplicate value.
    - Hanya boleh salah satu Candidate Key yang bisa menjadi Primary Key.

- **Alternate Key**
    - key yang bisa digunakan menjadi primary key.
    - Pada dasarnya, Key ini merupakan candidate key yang tidak dijadikan  primary key.

- **Unique Key**
    - Kumpulan dari satu atau lebih fields/columns di sebuah table database yang secara unik mengidentifikasi sebuah record dalam table database tersebut.
    - Hampir sama dengan Primary key, namun value dari Unique Key bisa berupa satu buah null value di dalam sebuah table database, dan Unique Key tidak bisa memiliki duplicate values

- **Foreign Key**
    - Field di sebuah table database yang menjadi Primary Key di table database lain.
    - Value dari Foreign key bisa menerima multiple null dan duplicate values.

### **Join Multiple Tables**
- **INNER JOIN**
    - Semua baris akan diambil dari kedua table yang akan di JOIN, selama columns cocok dengan kondisi yang sudah di tentukan.
    - Memungkinkan baris dari salah satu tabel muncul di hasil jika dan hanya jika kedua tabel memenuhi kondisi yang ditentukan dalam klausa ON.
- **LEFT JOIN**
    - Pada JOIN ini, semua records dari table di sisi kiri JOIN statement akan di pilih.
    - Jika record yang di pilih dari table kiri tidak memiliki record yang cocok pada table JOIN yang kanan, maka record tersebut masih dipilih, dan kolom pada table yang kanan akan bernilai NULL.
- **RIGHT JOIN**
    - Pada JOIN ini, semua records dari table di sisi kiri JOIN statement akan di pilih, bahkan jika table di sebelah kiri tidak memiliki record yang cocok.

### **Aggregate Functions**
Mengambil satu nilai setelah melakukan perhitungan pada sekumpulan nilai
- Type of Aggregate Functions
    - MAX
        <div align="justify">fungsi mengembalikan nilai terbesar dari kolom yang dipilih.

        ```
        SELECT MAX(column_name) FROM table_name WHERE condition;
        ```
    - MIN
        <div align="justify">fungsi mengembalikan nilai terkecil dari kolom yang dipilih.

        ```
        SELECT MIN(column_name) FROM table_name WHERE condition;
        ```
    - SUM
        <div align="justify">fungsi mengembalikan jumlah total kolom numerik.

        ```
        SELECT SUM(column_name) FROM table_name WHERE condition;
        ```
    - COUNT
        <div align="justify">fungsi mengembalikan jumlah baris yang cocok dengan kriteria yang ditentukan.

        ```
        SELECT COUNT(column_name) FROM table_name WHERE condition;
        ```
    - AVG
        <div align="justify">fungsi mengembalikan nilai rata-rata kolom numerik

        ```
        SELECT AVG(column_name) FROM table_name WHERE condition;
        ```
- UNION
    - Digunakan untuk menggabungkan kumpulan hasil dari dua atau lebih pernyataan SELECT.
    - Setiap pernyataan SELECT dalam UNION harus memiliki jumlah kolom yang sama
    - Kolom juga harus memiliki tipe data yang serupa
    - Kolom dalam setiap pernyataan SELECT juga harus dalam urutan yang sama

    ```
    SELECT column_name(s) FROM tablel
    UNION
    SELECT column_name(s) FROM table2;
    ```

- GROUP BY
    - Mengelompokkan baris yang memiliki nilai yang sama ke dalam baris ringkasan
    - Sering digunakan dengan fungsi agregat untuk mengelompokkan kumpulan hasil dengan satu atau lebih kolom.

    ```
    SELECT column_name(s)
    FROM table_name
    WHERE condition
    GROUP BY column_name(s);
    ```

- HAVING
    - HAVING ditambahkan ke SQL karena kata kunci WHERE tidak dapat digunakan dengan aggregate functions.

    ```
    SELECT column_name(s)
    FROM table_name
    WHERE condition
    GROUP BY column_name(s)
    HAVING condition
    ORDER BY column_name(s);
    ```
## **EXPRESS JS MIDDLEWARE AUTHENTICATION & AUTHORIZATION**
### **Authentication**
Merupakan metode terhadap seorang pengguna mengkonfirmasi sebagai pengguna valid yang dapat mengakses sebuah akun atau informasi tertentu

### **Authorization**
Merupakan proses penentuan terhadap pengguna yang terautentikasi tersebut diizinkan atau ditolak untuk melakukan satu atau lebih akses terhadap sistem.

### **Encryption**
Merupakan proses pengubahan data menjadi format yang tidak bisa dibaca terkecuali apabila ada seseorang yang memiliki kunci untuk mengubah kembali data yang terenkripsi

### **Jenis Autentikasi**
- **Single Factor Authentication**
    <div align="justify">Autentikasi yang sangat sederhana dan banyak digunakan di masa sekarang. Autentikasi ini berupa memasukan sebuah identitas seperti password dan username.

- **Two Factor Authentication**
    <div align="justify">Autentikasi ini dibuat setelah Single Factor Authentication dipakai yaitu adanya tambahan autentikasi seperti OTP dan sidik jari atau wajah.

- **Multi Factor Authentication**
    <div align="justify">Autentikasi yang mewajibkan pengguna untuk memverifikasi 3 jenis identitas seperti ID pengguna (password dan username), sidik jari, dan beberapa pertanyaan yang berhubungan dengan pengguna.


## **BUILD WEB SERVICE and RESTFUL API WITH EXPRESS & SEQUELIZE**
### **Sequelize**
Sequelize adalah ORM (Object Relational Mapping) Node JS yang berbasis promise. Sequelize mendukung sebagian besar relational Database seperti MySQL, PostgresQL, MariaDB, SQLite dan Miscrosoft SQL Server.
Dengan fitur fitur di Sequelize, kita bisa mengelola dan mengatur data di database kita dengan cepat, dan efisien

### **Installation Sequelize**
- Install Sequelize-cli
     <div align="justify">menginstall sequelize cli agar dapat menjalankan generator menggunakan terminal sehingga lebih mudah.
    
    ```
    npm install -g sequelize-cli
    ```
- Install Sequelize
    <div align="justify">Ketika kita melakukan inisiasi project kita pertama perlu menginstall sequelize menggunakan npm install sequelize dan perlu menginstall driver sql yang kita butuhkan

    ```
    Installing by NPM
    npm install --save sequelize
    install Driver Database
    npm install --save mysql
    ```
### **Membuat CRUD Dengan Express dan Sequelize**
Setelah Model tersedia, maka model tersebut bisa kita gunakan untuk membuat CRUD.

Beberapa endpoint RESTFul :
- Get All Todos
    <div align="justify">Untuk Kita akan membuat sebuah routing entuk get all todo dengan syntax berikut 

    ```javascript
    const todoModel = require('./models').Todo;

    app.get('/todos', async function (req, res){
        try{
            const todos = await todoModel.findAll();

            res.status(200).json(todos);
        }catch (error) {
            res.status(500).json({
                massage : error.massage || "internal server error"
            });
        }
    });
    ```
- Get Todo Detail By Id
    <div align="justify">Untuk Kita akan membuat sebuah routing entuk get detail todo berdasarkan Id todo dengan syntax berikut :

    ```javascript
    const todoModel = require('./models').Todo;

    app.get('/todos/:todoId', async function (req, res){
        try{
            const todos = await todoModel.findOne({ id: Number(todoId)});

            res.status(200).json(todos);
        }catch (error) {
            res.status(500).json({
                massage : error.massage || "internal server error"
            });
        }
    });
    ```


