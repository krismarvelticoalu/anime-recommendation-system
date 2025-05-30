# Laporan Proyek Machine Learning - Krismarvel Ticoalu

## Project Overview

Anime merupakan industri animasi yang berasal dari Jepang yang sangat diminati oleh banyak orang di seluruh dunia khususnya anak muda. Dalam beberapa tahun terakhir, anime mengalami peningkatan jumlah penonton di seluruh dunia terutama pada saat dunia dilanda COVID-19 [1]. Dengan meningkatnya minat orang banyak terhadap anime, permintaan akan tontonan anime semakin melonjak seiring dengan bertambahnya penonton baru. Penonton baru sering melakukan hal yang sama, yaitu meminta rekomendasi anime baik kepada orang secara langsung maupun melalui dunia maya. Masalahnya, tidak selalu anime yang direkomendasikan orang lain merupakan anime yang cocok dengan penonton baru sedangkan pilihan anime yang tersedia sangatlah banyak sehingga penonton baru sering susah memilih anime sendiri [2]. Belum lagi setiap orang tentunya memiliki kesibukan masing-masing sehingga tidak selalu orang lain dapat memberikan rekomendasi anime kepada penonton baru. Hadirnya teknologi seperti sistem rekomendasi dapat membantu mengatasi masalah tersebut. Dengan sistem rekomendasi anime, penonton baru tidak perlu menunggu lama untuk mendapatkan rekomendasi anime. Selain itu, rekomendasi anime yang diberikan akan selalui menyesuaikan dengan minat penonton baru tersebt. Apabila penonton sempat menonton satu anime dan dia menyukai anime tersebut, penonton tersebut dapat menggunakan sistem rekomendasi untuk mencari rekomendasi anime yang mirip dengan anime yang dia sukai tersebut. Semuanya ini dapat dilakukan dengan cepat karena mengandalkan sistem. Dampak secara ekonomi dari sistem rekomendasi ini juga dapat dipertimbangkan. Dengan adanya sistem rekomendasi, suatu platform penyedia tontonan anime dapat menarik lebih banyak penonton baru karena kemudahan dalam memilih anime yang merupakan manfaat daripada sistem rekomendasi.

## Business Understanding

### Problem Statements
- **Berdasarkan data pengguna, bagaimana membuat sistem rekomendasi anime yang dipersonalisasi dengan teknik content-based filtering?**
Proyek ini akan mencoba menjawab cara membuat sistem rekomendasi anime yang dipersonalisasi dengan teknik content-based filtering.
- **Bagaimana mengevaluasi sistem rekomendasi anime yang dibuat dengan pendekatan content-based filtering?**
Proyek ini akan mencoba menjawab cara mengevaluasi sistem rekomendasi anime yang dibuat dengan pendekatan content-based filtering.

### Goals
- **Mengembangkan sistem rekomendasi anime yang dipersonalisasi menggunakan teknik content-based filtering.**
Sistem rekomendasi anime akan dibuat menggunakan teknik content-based filtering.
- **Mengevaluasi sistem rekomendasi anime yang dibuat dengan pendekatan content-based filtering menggunakan metrik yang ditentukan.**
Sistem rekomendasi yang dibuat akan dievaluasi menggunakan metrik yang ditentukan.

## Data Understanding
Dataset yang digunakan pada proyek ini adalah [Anime Recommendation Database 2020](https://www.kaggle.com/datasets/hernan4444/anime-recommendation-database-2020/data?select=rating_complete.csv) yang dipublikasikan melalui situs [Kaggle](https://www.kaggle.com/). Terdapat beberapa file csv yaitu anime.csv, anime_with_synopsis.csv, animelist.csv, rating_complete.csv, dan watching_status.csv. File yang digunakan dalam proyek ini adalah anime.csv dan animelist.csv. Jumlah sampel atau baris data pada anime.csv adalah 17562 baris dengan 35 kolom sedangkan pada animelist.csv terdapat 109 juta baris dan 5 kolom. Kondisi data sangat baik, tidak ada missing value maupun data duplikat setelah dicek menggunakan **.isnull().sum()** dan **.duplicated().sum()**. Dataset dikumpulkan dengan web scraping yang telah dilakukan pada rentang waktu 26 Februari 2020 hingga 20 Maret

### Variabel-variabel pada dataset anime.csv adalah sebagai berikut:
- **MAL_ID**: ID MyAnimelist dari anime tersebut. (misalnya 1)
- **Name**: nama lengkap anime tersebut. (misalnya Cowboy Bebop)
- **Score**: skor rata-rata anime yang diberikan dari semua pengguna dalam basis data MyAnimelist. (misalnya 8,78)
- **Genres**: daftar genre yang dipisahkan koma untuk anime ini. (misalnya Aksi, Petualangan, Komedi, Drama, Sci-Fi, Luar Angkasa)
- **English name**: nama lengkap anime dalam bahasa Inggris. (misalnya Cowboy Bebop)
- **Japanese name**: nama lengkap anime dalam bahasa Jepang. (misalnya カウボーイビバップ)
- **Type**: TV, film, OVA, dll. (misalnya TV)
- **Episodes**: jumlah bab. (misalnya 26)
- **Aired**: tanggal siaran. (misalnya 3 April 1998 hingga 24 April 1999)
- **Premiered**: penayangan perdana musim. (misalnya Musim semi 1998)
- **Producers**: daftar produser yang dipisahkan koma (misalnya Bandai Visual)
- **Licensors**: daftar pemberi lisensi yang dipisahkan koma (misalnya Funimation, Bandai Entertainment)
- **Studios**: daftar studio yang dipisahkan koma (misalnya Sunrise)
- **Source**: Manga, Novel ringan, Buku, dll. (misalnya Orisinal)
- **Duration**: durasi anime per episode (misalnya 24 menit per ep.)
- **Rating**: tingkat usia (misalnya R - 17+ (kekerasan & kata-kata kasar))
- **Ranked**: posisi berdasarkan skor. (misalnya 28)
- **Popularity**: posisi berdasarkan jumlah pengguna yang telah menambahkan anime ke daftar mereka. (misalnya 39)
- **Members**: jumlah anggota komunitas yang berada dalam "grup" anime ini. (misalnya 1251960)
- **Favorites**: jumlah pengguna yang menjadikan anime tersebut sebagai "favorit". (misalnya 61.971)
- **Watching**: jumlah pengguna yang sedang menonton anime tersebut. (misalnya 105808)
- **Completed**: jumlah pengguna yang telah menyelesaikan anime tersebut. (misalnya 718161)
- **On-Hold**: jumlah pengguna yang menunda anime tersebut. (misalnya 71513)
- **Dropped**: jumlah pengguna yang telah menghentikan anime tersebut. (misalnya 26678)
- **Plan to Watch**: jumlah pengguna yang berencana untuk menonton anime tersebut. (mis. 329800)
- **Score-10**: jumlah pengguna yang mendapat skor 10. (mis. 229170)
- **Score-9**: jumlah pengguna yang mendapat skor 9. (mis. 182126)
- **Score-8**: jumlah pengguna yang mendapat skor 8. (mis. 131625)
- **Score-7**: jumlah pengguna yang mendapat skor 7. (mis. 62330)
- **Score-6**: jumlah pengguna yang mendapat skor 6. (mis. 20688)
- **Score-5**: jumlah pengguna yang mendapat skor 5. (mis. 8904)
- **Score-4**: jumlah pengguna yang mendapat skor 4. (mis. 3184)
- **Score-3**: jumlah pengguna yang mendapat skor 3. (mis. 1357)
- **Score-2:** jumlah pengguna yang mendapat skor 2. (misalnya 741)
- **Score-1**: jumlah pengguna yang mendapat skor 1. (misalnya 1580)

### Variabel-variabel pada dataset animelist.csv adalah sebagai berikut:
- **user_id**: ID pengguna yang dibuat secara acak dan tidak dapat diidentifikasi.
- **anime_id**: ID MyAnimeList dari anime tersebut. (misalnya 1).
- **score**: skor antara 1 hingga 10 yang diberikan oleh pengguna. 0 jika pengguna tidak memberikan skor. (misalnya 10)
- **watching_status**: ID status dari anime ini dalam daftar anime pengguna ini. (misalnya 2)
- **watched_episodes**: jumlah episode yang ditonton oleh pengguna. (misalnya 24)

### Exploratory Data Analysis
- **Visualisasi distribusi rating anime**
![](https://images2.imgbox.com/7c/00/SrT5Mfcn_o.png)
- **Visualisasi distribusi tipe anime**
![](https://images2.imgbox.com/19/8c/s2VJ3mvU_o.png)
- **Visualisasi distribusi sumber adaptasi anime**
![](https://images2.imgbox.com/e9/cb/cQEksbHQ_o.png)

## Data Preparation
Tahapan-tahapan yang dilakukan pada Data Preparation adalah sebagai berikut.
- **Menghilangkan data dengan nilai Unknown dari data genre**
    Tahapan ini diperlukan agar tidak ada nilai Unknown yang akan teridentifikasi sebagai genre anime.
    ```
    anime = anime[anime['Genres'] != 'Unknown']
    ```
- **Menyimpan dataframe anime dengan kolom MAL_ID, Name, Genres**
    Tahapan ini diperlukan untuk menyederhanakan dataframe anime menjadi 3 kolom yang diperlukan saja
    ```
    all_anime = anime[['MAL_ID', 'Name', 'Genres']]
    ```

- **Mengurutkan anime berdasarkan MAL_ID**
    Tahapan ini diperlukan agar data tampil berurutan.
    ```
    sorted_anime = all_anime.sort_values('MAL_ID', ascending=True)
    sorted_anime
    ```

- **Memetakan setiap anime dengan 1 genre saja**
    Tahapan ini diperlukan agar memudahkan pada saat evaluasi yaitu hanya dengan membandingkan data tunggal yaitu 1 genre saja dan bukan kombinasi dari banyak genre.
    ```
    sorted_anime['Genres'] = sorted_anime['Genres'].apply(lambda x: x.split(', ')[0])
    sorted_anime['Genres']
    ```

- **Mengonversi data series ‘anime_id’, ‘Name’, ‘Genres’ menjadi dalam bentuk list**
    Tahapan ini diperlukan agar memudahkan dalam menghitung jumlah data mal_id, anime_name, dan anime genre
    ```
    mal_id = sorted_anime['MAL_ID'].tolist()
    
    anime_name = sorted_anime['Name'].tolist()
    
    anime_genre = sorted_anime['Genres'].tolist()
    
    print(len(mal_id))
    print(len(anime_name))
    print(len(anime_genre))
    ```

    
- **Membuat Dataframe baru dengan nama kolom id, anime_name, dan genre**
    Tahapan ini dilakukan untuk menyederhanakan nama kolom yaitu dengan membuat dataframe dengan nama kolom yang baru sehingga lebih mudah untuk direferensikan dan dibaca (MAL_ID menjadi id, Name menjadi anime_name, dan Genres menjadi genre)
    ```
    anime_new = pd.DataFrame({
        'id': MAL_ID,
        'anime_name': anime_name,
        'genre': anime_genre
    })
    anime_new
    ```
- **Assign dataframe anime_new ke dalam variabel data kemudian cek 5 sampelnya**
    Tahapan ini dilakukan agar dataframe dapat diakses menggunakan variabel data yang lebih mudah diingat, dibaca dan direferensikan.
    ```
    data = anime_new
    data.sample(5)
    ```
- **Menerapkan TF-IDF Vectorizer terhadap data genre**
    Tahapan ini dilakukan untuk menghitung idf pada setiap genre. Setiap genre akan direpresentasikan sebagai vektor numerik.
    ```
    from sklearn.feature_extraction.text import TfidfVectorizer
 
    # Inisialisasi TfidfVectorizer
    tf = TfidfVectorizer(token_pattern=r'(?u)\b\w\w+\s*-*\w+\s*\w+\b')
     
    # Melakukan perhitungan idf pada data genre
    tf.fit(data['genre']) 
     
    # Mapping array dari fitur index integer ke fitur nama
    tf.get_feature_names_out() 
    ```
- **Melakukan fit lalu ditransformasikan ke bentuk matrix dan melihat ukuran matrix tfidf**
    Tahapan ini perlu dilakukan untuk mendapatkan matrix tfidf yang merupakan representasi vektor daripada data genre yang akan digunakan ketika menghitung cosine similarity.
    ```
    tfidf_matrix = tf.fit_transform(data['genre']) 
 
    tfidf_matrix.shape 
    ```
- **Mengubah vektor tf-idf dalam bentuk matriks menjadi bentuk dense dengan fungsi todense()**
    Tahapan ini perlu dilakukan agar matrix siap digunakan untuk dilakukan perhitungan cosine similarity.
    ```
    tfidf_matrix.todense()
    ```
- **Membuat dataframe untuk melihat tf-idf matrix**
    Tahapan ini dilakukan agar korelasi antara nama anime dengan genre dapat dilihat melalui representasi angka 0 dan 1. Ini memudahkan kita untuk memahami tfidf matrix yang telah dibuat.
    ```
    # Kolom diisi dengan genre
    # Baris diisi dengan nama anime
 
    pd.DataFrame(
        tfidf_matrix.todense(), 
        columns=tf.get_feature_names_out(),
        index=data.anime_name
    ).sample(10, axis=0)
    ```

## Modeling
Pendekatan pengembangan sistem rekomendasi pada proyek ini adalah content-based filtering. Content-based filtering mempelajari profil minat pengguna baru berdasarkan data dari objek yang telah dinilai pengguna [3]. Algoritma ini bekerja dengan menyarankan item serupa yang pernah disukai di masa lalu atau sedang dilihat di masa kini kepada pengguna [3]. Semakin banyak informasi yang diberikan pengguna, semakin baik akurasi sistem rekomendasi [3].

Pada proyek ini, sistem akan merekomendasikan anime berdasarkan satu anime yang dipilih. Berdasarkan anime yang dipilih ini, akan direkomendasikan anime-anime yang similar atau mirip. Kemiripan atau similarity antar anime ditentukan dengan menghitung cosine similarity.
```
from sklearn.metrics.pairwise import cosine_similarity
 
cosine_sim = cosine_similarity(tfidf_matrix) 
cosine_sim
```
Setelah itu, hasil perhitungan cosine similarity dimasukkan ke dalam dataframe baru agar dapat dilihat similarity antar anime.
```
cosine_sim_df = pd.DataFrame(cosine_sim, index=data['anime_name'], columns=data['anime_name'])
print('Shape:', cosine_sim_df.shape)
 
cosine_sim_df.sample(5, axis=1).sample(10, axis=0)
```
Kemudian, fungsi untuk mendapat rekomendasi didefinisikan.
```
def anime_recommendations(nama_anime, similarity_data=cosine_sim_df, items=data[['anime_name', 'genre']], k=5):
    
    index = similarity_data.loc[:,nama_anime].to_numpy().argpartition(
        range(-1, -k, -1))
    
    closest = similarity_data.columns[index[-1:-(k+2):-1]]

    closest = closest.drop(nama_anime, errors='ignore')
    
    return pd.DataFrame(closest).merge(items).head(k)
```
Anime yang dipilih sebagai preferensi pengguna pada proyek ini adalah Slam Dunk yang memiliki genre Comedy. 
```
slam_dunk = data[data.anime_name.eq('Slam Dunk')]

slam_dunk_genre = slam_dunk['genre'].values[0]

slam_dunk
```
Apabila k = 10, maka rekomendasi anime yang akan diberikan berjumlah 10.
```
k = 10
recommendations_df = anime_recommendations('Slam Dunk', k=k)
recommendations_df
```
Berikut ini adalah top 10 rekomendasi anime yang serupa atau mirip dengan anime Slam Dunk.
![top 10 recommendation](https://images2.imgbox.com/ec/76/yFkGPF7Q_o.png)

## Evaluation
Evaluasi dilakukan dengan menggunakan metrik evaluasi Precision@K dan menampilkan hasil perhitungan metrik tersebut. Nilai Precision@K merupakan metrik evaluasi yang digunakan untuk mengevaluasi sistem rekomendasi. Nilai Precision@K dihitung dengan membagi jumlah item rekomendasi yang relevan dengan jumlah item yang direkomendasikan.
![Formula Precision@K](https://cdn.prod.website-files.com/660ef16a9e0687d9cc27474a/662c4327f27ee08d3e4d4b34_65777ee1fd55288155f28d37_precision_recall_k2.png)
Proyek ini berhasil menghasilkan sistem rekomendasi anime yang dipersonalisasi menggunakan teknik content-based filtering dengan nilai Precision@K yaitu 1.0. Rekomendasi anime yang relevan ditentukan dengan melihat apakah genre yang dimiliki suatu rekomendasi anime sama dengan genre anime yang dipilih yaitu Slam Dunk. Jumlah rekomendasi anime yang relevan dari seluruh rekomendasi anime adalah 10. Jumlah total rekomendasi anime yang ditentukan pada proyek ini adalah 10. Oleh karena itu, nilai Precision@K untuk sistem rekomendasi pada proyek ini adalah 1.0.
```
rekomendasi_relevan = []
for row in recommendations_df.values:
  if row[1] == slam_dunk_genre:
    rekomendasi_relevan.append(row[0])
    
total_rekomendasi_relevan = len(rekomendasi_relevan)
total_rekomendasi = k

precision = total_rekomendasi_relevan / total_rekomendasi
print("Nilai precision:", precision)

# Output
Nilai precision: 1.0
```


**Daftar Pustaka**:
[1] P. Brzeski, “How Japanese Anime Became the World’s Most Bankable Genre,” The Hollywood Reporter, May 17, 2022. https://www.hollywoodreporter.com/business/business-news/japanese-anime-worlds-most-bankable-genre-1235146810/
[2] J. Chen, “The Investigation on Anime-Themed Recommendation Systems,” Highlights in Science Engineering and Technology, vol. 81, pp. 121–131, Jan. 2024, doi: https://doi.org/10.54097/36drh331.
[3] Dicoding Indonesia, “Content Based Filtering | Machine Learning Terapan | Dicoding Indonesia,” Dicoding.com, 2017. https://www.dicoding.com/academies/319/tutorials/17116 (accessed May 30, 2025).
**---Ini adalah bagian akhir laporan---**
