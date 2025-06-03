# Laporan Proyek Machine Learning - Krismarvel Ticoalu

## Project Overview

Anime merupakan industri animasi yang berasal dari Jepang yang sangat diminati oleh banyak orang di seluruh dunia khususnya anak muda. Dalam beberapa tahun terakhir, anime mengalami peningkatan jumlah penonton di seluruh dunia terutama pada saat dunia dilanda COVID-19 [1]. Dengan meningkatnya minat orang banyak terhadap anime, permintaan akan tontonan anime semakin melonjak seiring dengan bertambahnya penonton baru. Penonton baru sering melakukan hal yang sama, yaitu meminta rekomendasi anime baik kepada orang secara langsung maupun melalui dunia maya. Masalahnya, tidak selalu anime yang direkomendasikan orang lain merupakan anime yang cocok dengan penonton baru sedangkan pilihan anime yang tersedia sangatlah banyak sehingga penonton baru sering susah memilih anime sendiri [2]. Belum lagi setiap orang tentunya memiliki kesibukan masing-masing sehingga tidak selalu orang lain dapat memberikan rekomendasi anime kepada penonton baru. Hadirnya teknologi seperti sistem rekomendasi dapat membantu mengatasi masalah tersebut. Dengan sistem rekomendasi anime, penonton baru tidak perlu menunggu lama untuk mendapatkan rekomendasi anime. Selain itu, rekomendasi anime yang diberikan akan selalui menyesuaikan dengan minat penonton baru tersebut. Apabila penonton sempat menonton satu anime dan dia menyukai anime tersebut, penonton tersebut dapat menggunakan sistem rekomendasi untuk mencari rekomendasi anime yang mirip dengan anime yang dia sukai tersebut. Semuanya ini dapat dilakukan dengan cepat karena mengandalkan sistem. Dampak secara ekonomi dari sistem rekomendasi ini juga dapat dipertimbangkan. Dengan adanya sistem rekomendasi, suatu platform penyedia tontonan anime dapat menarik lebih banyak penonton baru karena kemudahan dalam memilih anime yang merupakan manfaat daripada sistem rekomendasi.

## Business Understanding

### Problem Statements
- **Berdasarkan data anime, bagaimana membuat sistem rekomendasi anime yang dapat diandalkan dengan teknik content-based filtering?**
Proyek ini akan mencoba menjawab cara membuat sistem rekomendasi anime yang dapat diandalkan dengan teknik content-based filtering.
- **Bagaimana mengevaluasi sistem rekomendasi anime yang dibuat dengan pendekatan content-based filtering?**
Proyek ini akan mencoba menjawab cara mengevaluasi sistem rekomendasi anime yang dibuat dengan pendekatan content-based filtering.

### Goals
- **Mengembangkan sistem rekomendasi anime yang dapat diandalkan menggunakan teknik content-based filtering.**
Sistem rekomendasi anime akan dibuat menggunakan teknik content-based filtering.
- **Mengevaluasi sistem rekomendasi anime yang dibuat dengan pendekatan content-based filtering menggunakan metrik yang ditentukan.**
Sistem rekomendasi yang dibuat akan dievaluasi menggunakan metrik yang ditentukan.

## Data Understanding
Dataset yang digunakan pada proyek ini adalah [Anime Recommendation Database 2020](https://www.kaggle.com/datasets/hernan4444/anime-recommendation-database-2020/data?select=rating_complete.csv) yang dipublikasikan melalui situs [Kaggle](https://www.kaggle.com/). Terdapat beberapa file csv yaitu anime.csv, anime_with_synopsis.csv, animelist.csv, rating_complete.csv, dan watching_status.csv. File yang digunakan dalam proyek ini adalah anime.csv. Jumlah sampel atau baris data pada anime.csv adalah 17562 baris dengan 35 kolom. Kondisi data sangat baik, tidak ada missing value maupun data duplikat setelah dicek menggunakan **.isnull().sum()** dan **.duplicated().sum()**.
![](https://images2.imgbox.com/8e/fc/gADtegoh_o.png) 

![](https://images2.imgbox.com/2b/5a/9cjYlhMw_o.png) 

![](https://images2.imgbox.com/8b/a3/G60LNynJ_o.png) 

Dataset dikumpulkan dengan web scraping yang telah dilakukan pada rentang waktu 26 Februari 2020 hingga 20 Maret 2020.

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

### Exploratory Data Analysis
- **Visualisasi distribusi rating anime**

![](https://images2.imgbox.com/7c/00/SrT5Mfcn_o.png)

**Insight:**
Dapat dilihat pada visualisasi di atas, rating anime paling banyak adalah "PG-13 - Teens 13 or older" atau bisa dikatakan remaja yang berumur 13 tahun ke atas. Rating anime terbanyak kedua adalah all ages artinya semua umur. Secara berurutan, rating anime terbanyak berikutnya adalah "PG - Children" atau anak-anak, "Rx - Hentai" atau anime panas khusus dewasa, "R - 17+ (violence & profanity) artinya mengandung kekerasan dan untuk umur 17 ke atas, dan terakhir adalah "R+ - Mild Nudity" artinya terdapat sedikit adegan yang menampilkan ketelanjangan.

- **Visualisasi distribusi tipe anime**

![](https://images2.imgbox.com/19/8c/s2VJ3mvU_o.png)

**Insight:**
Berdasarkan visualisasi data di atas, tipe anime paling banyak adalah TV (anime yang tayang di TV) diikuti dengan OVA (dipublikasikan langsung dalam format video), Movie (anime yang tampil di layar lebar), Special (biasanya episode ekstra daripada seri anime yang ada), ONA (anime yang dipublikasikan langsung di internet), dan Music (anime yang merupakan video musik, musik latar belakang, dsb)

- **Visualisasi distribusi sumber adaptasi anime**

![](https://images2.imgbox.com/e9/cb/cQEksbHQ_o.png)

**Insight:**
Berdasarkan visualisasi data di atas, dapat dilihat bahwa sumber adaptasi anime paling banyak adalah Original artinya anime tidak diadaptasikan dari sumber manapun dan langsung dipublikasikan sebagai anime. Sumber adaptasi paling banyak berikutnya adalah Manga (komik jepang) dan diikuti oleh Visual Novel, Game, Light Novel, Other (lainnya/selain yang disebutkan), Novel, Music, 4-koma Manga, Web Manga, Picture book, Book, Card game, Digital manga, dan terakhir adalah Radio.

## Data Preparation
Tahapan-tahapan yang dilakukan pada Data Preparation adalah sebagai berikut.
- **Menyimpan dataframe anime dengan 3 kolom yaitu MAL_ID, Name, dan Genres ke dalam variabel all_anime.**
    Tahapan ini diperlukan untuk menyederhanakan dataframe anime menjadi 3 kolom saja sehingga tidak ada data yang tidak diperlukan dalam proses data preparation hingga modeling.
    ```
    all_anime = anime[['MAL_ID', 'Name', 'Genres']]
    ```
- **Menghilangkan data dengan nilai Unknown dari kolom Genres**
    Tahapan ini diperlukan agar tidak ada nilai Unknown yang akan teridentifikasi sebagai genre anime.
    ```
    anime = anime[anime['Genres'] != 'Unknown']
    ```

- **Mengurutkan anime berdasarkan MAL_ID**
    Tahapan ini diperlukan agar data tampil berurutan.
    ```
    sorted_anime = all_anime.sort_values('MAL_ID', ascending=True)
    sorted_anime
    ```
    
- **Assign dataframe sorted_anime ke dalam variabel data kemudian cek 5 sampelnya**
    Tahapan ini dilakukan agar dataframe dapat diakses menggunakan nama variabel yang lebih deskriptif yang menunjukkan ini merupakan data yang akan dipakai pada tahap modeling.
    ```
    data = sorted_anime
    data.sample(5)
    ```
- **Mengnisialisasi TfidfVectorizer**
    Tahapan ini penting dilakukan karena instansi daripada TfidVectorizer akan digunakan untuk memanggil method fit_transform untuk mengubah data genre ke dalam bentuk vektor.
    ```
    tf = TfidfVectorizer(token_pattern=r'(?u)\b\w\w+\s*-*\w+\s*\w+\b')
    ```
- **Melakukan fit lalu ditransformasikan ke bentuk matrix dan melihat bentuk matrix tfidf**
    Tahapan ini penting dilakukan karena data genre dari setiap anime perlu diubah ke dalam bentuk vektor agar bisa dilakukan perhitungan cosine similarity. Perhitungan cosine similarity tidak dapat dilakukan pada data dalam bentuk atau format string/object.
    ```
    tfidf_matrix = tf.fit_transform(data['Genres'])

    tfidf_matrix.shape
    ```
- **Membuat dataframe untuk melihat tf-idf matrix (kolom diisi dengan genre dan baris diisi dengan nama anime) setelah itu mengambil 10 sampel kemudian ditampilkan.**
    Tahapan ini penting dilakukan agar memudahkan kita dalam melihat setiap vector daripada setiap anime untuk setiap genrenya.
    ```
    matrix_df = pd.DataFrame(
        tfidf_matrix.todense(),
        columns=tf.get_feature_names_out(),
        index=data.Name
    ).sample(10, axis=0)
    matrix_df
    ```

## Modeling
Pendekatan pengembangan sistem rekomendasi pada proyek ini adalah content-based filtering. Content-based filtering mempelajari profil minat pengguna baru berdasarkan data dari objek yang telah dinilai pengguna [3]. Algoritma ini bekerja dengan menyarankan item serupa yang pernah disukai di masa lalu atau sedang dilihat di masa kini kepada pengguna [3]. Semakin banyak informasi yang diberikan pengguna, semakin baik akurasi sistem rekomendasi [3].

Pada proyek ini, sistem akan merekomendasikan anime berdasarkan satu anime yang dipilih. Berdasarkan anime yang dipilih ini, akan direkomendasikan anime-anime yang similar atau mirip. Kemiripan atau similarity antar anime ditentukan dengan menghitung cosine similarity.
```
cosine_sim = cosine_similarity(tfidf_matrix) 
cosine_sim
```
Setelah itu, hasil perhitungan cosine similarity dimasukkan ke dalam dataframe baru agar dapat dilihat similarity antar anime.
```
cosine_sim_df = pd.DataFrame(cosine_sim, index=data['Name'], columns=data['Name'])
print('Shape:', cosine_sim_df.shape)
 
cosine_sim_df.sample(5, axis=1).sample(10, axis=0)
```
Kemudian, fungsi untuk mendapat rekomendasi didefinisikan.
```
def anime_recommendations(nama_anime, similarity_data=cosine_sim_df, items=data[['Name', 'Genres']], k=5):
    
    index = similarity_data.loc[:,nama_anime].to_numpy().argpartition(
        range(-1, -k, -1))
    
    closest = similarity_data.columns[index[-1:-(k+2):-1]]

    closest = closest.drop(nama_anime, errors='ignore')
    
    return pd.DataFrame(closest).merge(items).head(k)
```
Anime yang dipilih sebagai preferensi pengguna pada proyek ini adalah Slam Dunk yang memiliki genre Comedy, Drama, School, Shounen, dan Sports. 
```
slam_dunk = data[data.anime_name.eq('Slam Dunk')]

slam_dunk_genre = slam_dunk['genre'].values
slam_dunk_genre = slam_dunk_genre[0].split(', ')

print(slam_dunk_genre)

# Output:
['Comedy', 'Drama', 'School', 'Shounen', 'Sports']
```
Apabila k = 100, maka rekomendasi anime yang akan diberikan berjumlah 100.
```
k = 100
recommendations_df = anime_recommendations('Slam Dunk', k=k)
recommendations_df
```
Berikut ini adalah top 100 rekomendasi anime yang serupa atau mirip dengan anime Slam Dunk.
![top 100 recommendation (1/5)](https://images2.imgbox.com/5b/6b/Q42YQ1og_o.jpeg)
![top 100 recommendation (2/5)](https://images2.imgbox.com/f8/39/Ko5YBGB3_o.jpeg)
![top 100 recommendation (3/5)](https://images2.imgbox.com/40/47/vsXIhFhT_o.jpeg)
![top 100 recommendation (4/5)](https://images2.imgbox.com/67/5e/6TIDFU90_o.jpeg)
![top 100 recommendation (5/5)](https://images2.imgbox.com/ac/58/kxtOhBZR_o.jpeg)

## Evaluation
Evaluasi dilakukan dengan menggunakan metrik evaluasi Precision@K dan menampilkan hasil perhitungan metrik tersebut. Nilai Precision@K merupakan metrik evaluasi yang digunakan untuk mengevaluasi sistem rekomendasi. Nilai Precision@K dihitung dengan membagi jumlah item rekomendasi yang relevan dengan jumlah item yang direkomendasikan.
![Formula Precision@K](https://cdn.prod.website-files.com/660ef16a9e0687d9cc27474a/662c4327f27ee08d3e4d4b34_65777ee1fd55288155f28d37_precision_recall_k2.png)

 Apabila suatu anime memiliki lebih dari 3 genre yang sama dengan Slam Dunk maka anime tersebut dikatakan relevan. Slam dunk sendiri memiliki 5 genre yaitu Comedy, Drama, School, Shounen, dan Sports. Jumlah rekomendasi anime yang relevan dari keseluruhan rekomendasi anime yang diberikan adalah 77.
```
rekomendasi_relevan = []

for row in recommendations_df.values:
  relevancy = 0
  for genre in row[1].split(', '):
    if genre in slam_dunk_genre:
      relevancy += 1
      
  if relevancy > 3:
      rekomendasi_relevan.append(row[0])

print("Jumlah rekomendasi relevan:", len(rekomendasi_relevan))

# Output
Jumlah rekomendasi relevan: 77
```
Jumlah total rekomendasi anime yang diberikan pada proyek ini adalah 100. Maka, 77 (rekomendasi relevan) dibagi dengan 100 (total rekomendasi). Dengan demikian, proyek ini berhasil menghasilkan sistem rekomendasi anime yang dipersonalisasi menggunakan teknik content-based filtering dengan nilai Precision@K yaitu 0,77.
```
total_rekomendasi_relevan = len(rekomendasi_relevan)
total_rekomendasi = k

precision = total_rekomendasi_relevan / total_rekomendasi
print("Nilai precision:", precision)

# Output
Nilai precision: 0.77
```

Berdasarkan hasil evaluasi yang ada, proyek ini berhasil mencapai goal yang pertama yaitu "Mengembangkan sistem rekomendasi anime yang dapat diandalkan menggunakan teknik content-based filtering". Proyek ini berhasil membuat sistem rekomendasi yang dapat memberikan rekomendasi anime yang akurat dan dapat diandalkan. Dengan demikian, problem statement yang pertama yaitu "Berdasarkan data anime, bagaimana membuat sistem rekomendasi anime yang dapat diandalkan dengan teknik content-based filtering?" dapat terjawab. 

Proyek ini juga berhasil mencapai goal kedua yaitu "Mengevaluasi sistem rekomendasi anime yang dibuat dengan pendekatan content-based filtering menggunakan metrik yang ditentukan." dengan menggunakan metrik Precision@K untuk mengevaluasi performa sistem rekomendasi sehingga problem statement yang kedua yaitu "Bagaimana mengevaluasi sistem rekomendasi anime yang dibuat dengan pendekatan content-based filtering?" telah terjawab.

Solusi pengembangan sistem rekomendasi dengan pendekatan content-based filtering jelas memiliki dampak yang dapat dirasakan oleh pengguna. Hal ini dapat dilihat melalui bagaimana sistem rekomendasi berhasil mencapai setiap goals dan menjawab setiap problem statements. Hasil evaluasi juga menunjukkan bahwa sistem rekomendasi berfungsi dengan baik sehingga kualitas performanya pasti akan berdampak bagi pengguna.


**Daftar Pustaka**:
[1] P. Brzeski, “How Japanese Anime Became the World’s Most Bankable Genre,” The Hollywood Reporter, May 17, 2022. https://www.hollywoodreporter.com/business/business-news/japanese-anime-worlds-most-bankable-genre-1235146810/

[2] J. Chen, “The Investigation on Anime-Themed Recommendation Systems,” Highlights in Science Engineering and Technology, vol. 81, pp. 121–131, Jan. 2024, doi: https://doi.org/10.54097/36drh331.

[3] Dicoding Indonesia, “Content Based Filtering | Machine Learning Terapan | Dicoding Indonesia,” Dicoding.com, 2017. https://www.dicoding.com/academies/319/tutorials/17116 (accessed May 30, 2025).

**---Ini adalah bagian akhir laporan---**
