# Laporan Proyek Machine Learning - Aliffa Agnur

## Project Overview

Dalam era digital saat ini, sistem rekomendasi memainkan peran penting dalam membantu pengguna menemukan produk atau layanan yang sesuai dengan preferensi mereka. Salah satu pendekatan yang efektif dalam pengembangan sistem rekomendasi adalah Neural Collaborative Filtering (NCF), yang menggabungkan teknik pembelajaran mendalam untuk memodelkan interaksi kompleks antara pengguna dan item. Selain itu, pendekatan hybrid yang menggabungkan Content-Based Filtering (CBF) dan Collaborative Filtering (CF) juga telah terbukti meningkatkan kualitas rekomendasi dengan memanfaatkan informasi konten dan pola interaksi pengguna. [[1]](https://ejurnal.itenas.ac.id/index.php/mindjournal/article/view/12447/0). 

jumlah konten anime yang tersedia di berbagai platform streaming semakin meningkat, sehingga pengguna seringkali kesulitan menemukan anime yang sesuai dengan preferensi mereka" didukung oleh beberapa sumber. Misalnya, artikel di Jurno.id mencatat bahwa kemajuan teknologi dan distribusi konten anime melalui berbagai platform, termasuk streaming Over the Top (OTT), telah mendorong pertumbuhan pasar anime secara signifikan. Selain itu, laporan dari Parrot Analytics menunjukkan bahwa meskipun anime menyumbang sekitar 6% dari total pendapatan streaming global pada tahun 2023, pangsa pasar ini diperkirakan akan terus berkembang seiring dengan pertumbuhan industri streaming secara keseluruhan. [[2]](https://www.parrotanalytics.com/insights/global-streaming-value-anime-netflix-crunchyroll-hulu/)
    
Mengenai penggunaan Neural Collaborative Filtering (NCF) dan pendekatan hybrid dalam sistem rekomendasi, hal ini didukung oleh penelitian yang menunjukkan bahwa NCF, yang memanfaatkan jaringan saraf dalam untuk memodelkan interaksi pengguna-item, dapat meningkatkan akurasi rekomendasi. Sebuah artikel di Medium menjelaskan bahwa NCF terutama digunakan untuk Collaborative Filtering, yang merekomendasikan item berdasarkan kesamaan preferensi pengguna tanpa fitur tambahan. Selain itu, penelitian yang dipublikasikan di MDPI mengemukakan bahwa sistem rekomendasi hybrid yang menggabungkan ontologi dengan NCF dapat meningkatkan kualitas rekomendasi dengan memadukan pendekatan berbasis pengetahuan dan data. [[3]](https://medium.com/data-science-in-your-pocket/recommendation-systems-using-neural-collaborative-filtering-ncf-explained-with-codes-21a97e48a2f7)
    
**Alasan Mengapa Proyek ini penting untuk diselesaikan :**

1. dengan melimpahnya konten anime di platform-platform tersebut, pengguna sering merasa kewalahan dalam mencari judul yang sesuai dengan preferensi mereka. Hal ini menekankan pentingnya sistem rekomendasi yang efektif untuk membantu pengguna menemukan anime yang relevan. Sebuah laporan menunjukkan bahwa sistem rekomendasi anime dapat meningkatkan keterlibatan pengguna dan retensi, dengan menawarkan rekomendasi yang dipersonalisasi sesuai dengan minat mereka. [[1]](https://jurnal.utu.ac.id/JTI/article/viewFile/7787/4290)

1. Pendekatan hybrid yang menggabungkan metode CF dan CBF telah terbukti meningkatkan kualitas rekomendasi. Sebuah penelitian menunjukkan bahwa pendekatan hybrid CF-CBF memberikan presisi tertinggi dalam rekomendasi lagu, yaitu 50,7%, dibandingkan dengan metode CF dan CBF secara terpisah. [[2]](https://repositori.telkomuniversity.ac.id/pustaka/files/177772/jurnal_eproc/sistem-rekomendasi-film-menggunakan-metode-hybrid-collaborative-filtering-dan-content-based-filtering.pdf)
2. Sistem rekomendasi sering menghadapi masalah cold-start, terutama ketika data pengguna baru terbatas. Dengan menggabungkan NCF dan pendekatan hybrid, sistem dapat memanfaatkan informasi konten dan interaksi pengguna untuk memberikan rekomendasi yang lebih akurat, bahkan untuk pengguna baru. Sebuah penelitian menunjukkan bahwa mengintegrasikan informasi tambahan tentang pengguna dan item ke dalam jaringan saraf yang dalam dapat mengurangi masalah cold-start. Pendekatan ini memungkinkan sistem untuk memberikan rekomendasi yang lebih akurat bahkan ketika data interaksi terbatas. [[3]](https://www.sciencedirect.com/science/article/abs/pii/S0957417419307717)
3. Selain itu, Magron dan Févotte (2021) mengembangkan metode Neural Content-Aware Collaborative Filtering yang menggabungkan pembelajaran mendalam untuk mengekstraksi fitur konten dan memodelkan interaksi antara pengguna dan item. Pendekatan ini efektif dalam mengatasi masalah cold-start [[4]](https://arxiv.org/abs/2102.12369)



## Business Understanding

Seiring dengan meningkatnya jumlah konten anime yang tersedia di berbagai platform streaming, pengguna sering kali kesulitan dalam menemukan anime yang sesuai dengan preferensi mereka. Tanpa adanya sistem rekomendasi yang efektif, pengguna mungkin melewatkan anime yang relevan, dan pengalaman menonton mereka menjadi kurang optimal. Hal ini dapat mengurangi tingkat kepuasan dan retensi pengguna, serta membatasi potensi pertumbuhan platform streaming tersebut. Di sisi lain, sistem rekomendasi yang kurang tepat juga dapat mengarah pada rekomendasi yang tidak sesuai dengan minat pengguna, baik dalam hal genre, tema, atau kualitas anime.

### Problem Statements

Menjelaskan pernyataan masalah:
- **Pernyataan Masalah 1:** Pengguna platform streaming anime kesulitan menemukan anime yang sesuai dengan preferensi mereka karena jumlah konten yang terus berkembang dan kurangnya rekomendasi yang relevan.
- **Pernyataan Masalah 2:** Sistem rekomendasi yang ada saat ini tidak mampu menangani masalah cold-start, baik untuk pengguna baru maupun anime baru yang belum memiliki cukup data interaksi.
- **Pernyataan Masalah 3:** Sistem rekomendasi yang ada cenderung memberikan rekomendasi yang terbatas pada genre atau tema yang sudah diketahui, mengurangi keberagaman pilihan yang dapat diterima oleh pengguna.

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- **Jawaban pernyataan masalah 1:** Mengembangkan sistem rekomendasi yang dapat memberikan rekomendasi anime yang lebih personal dan relevan dengan memanfaatkan gabungan metode Content-Based Filtering (CBF) dan Collaborative Filtering (CF) untuk mengidentifikasi preferensi pengguna dan memberikan rekomendasi yang sesuai.
- **Jawaban pernyataan masalah 2:** Mengatasi masalah cold-start dengan menggabungkan CBF dan CF dalam pendekatan hybrid serta menggunakan teknik Neural Collaborative Filtering (NCF) yang memungkinkan sistem mempelajari preferensi pengguna secara lebih efisien, bahkan dengan data interaksi yang terbatas.
- **Jawaban pernyataan masalah 3:** Mengembangkan sistem rekomendasi yang lebih beragam dan akurat dengan memanfaatkan algoritma hybrid yang dapat mengenali pola baru berdasarkan konten dan interaksi sosial, sehingga menghasilkan rekomendasi yang lebih variatif dan tidak terbatas pada satu genre atau tema tertentu.

Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

### Solution statements
1. Menggunakan **Hybrid Filtering (CBF + CF)**. Pendekatan ini menggabungkan teknik Content-Based Filtering (CBF) dan Collaborative Filtering (CF). CBF berfokus pada rekomendasi berdasarkan kesamaan konten (seperti genre dan tema), sementara CF melihat pola interaksi antar pengguna dan anime.
2. Menggunakan Neural **Collaborative Filtering (NCF)**. NCF menggunakan pembelajaran mendalam untuk memodelkan hubungan antara pengguna dan anime. Dengan menggunakan jaringan saraf, NCF dapat menangkap pola interaksi yang lebih kompleks yang tidak dapat dijangkau oleh metode CF tradisional.


## Data Understanding
Dataset ini didapatkan dari [Anime Recommendation System](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database)

Dataset Anime ini terdiri dari 2 Tabel utama, Yaitu Data *User* dan data *Anime*.

  ### Fitur yg terdapat dalam data Anime:
| Kolom       | Deskripsi                                                                |
|-------------|--------------------------------------------------------------------------|
| anime_id    | ID unik untuk setiap anime.                                              |
| name        | Nama dari anime.                                                        |
| genre       | Genre atau kategori anime, seperti Drama, Aksi, Komedi, dll.            |
| type        | Jenis anime, seperti TV, Movie, atau OVA.                               |
| episodes    | Jumlah episode anime tersebut.                                          |
| rating      | Rating rata-rata anime, biasanya dalam rentang 1–10.                    |
| members     | Jumlah anggota yang memberi rating atau menonton anime.                 |

**Data Anime ini terdiri dari 12294 baris dan 7 kolom**

### Fitur yg terdapat dalam data User : 
| Kolom     | Deskripsi                                                              |
|-----------|------------------------------------------------------------------------|
| user_id   | ID unik untuk setiap pengguna.                                         |
| anime_id  | ID anime yang diberi rating oleh pengguna.                             |
| rating    | Rating yang diberikan oleh pengguna terhadap anime tertentu (biasanya antara 1-10). |

**Data User ini terdiri dari 7813737 baris dan 3 kolom**

## Solutions

### 1. Univariate Analysis

  - **Type/Category Distribution**
![TypeDistribution](https://github.com/user-attachments/assets/94a6af92-9f9e-428f-b5c7-9a1e382e7772)
<br>  <br> <br>
  - **Anime with Most Episodes**
    ![output](https://github.com/user-attachments/assets/490cd28f-bf2b-4b59-ab82-af71b3cdaf9c)
    <br> <br>
    
  - **Genre Distribution**
    ![output](https://github.com/user-attachments/assets/6f54ad04-c586-4d5f-a82c-b04967b13f28)
    ![output](https://github.com/user-attachments/assets/b62bf050-5b7b-4534-a951-dde07b91c4e3)
<br> <br>
  - **Most Popular Anime**
    ![output](https://github.com/user-attachments/assets/554ca727-6f35-437e-ab19-b266a58142c3)
    
| name                               | rating |
|------------------------------------|--------|
| Hunter x Hunter (2011)             | 9.13   |
| Ginga Eiyuu Densetsu               | 9.11   |
| Gintama                            | 9.04   |
| Slam Dunk                          | 8.56   |
| Yuu☆Yuu☆Hakusho                   | 8.47   |
| Katekyo Hitman Reborn!             | 8.37   |
| Dragon Ball Z                      | 8.32   |
| Saiki Kusuo no Ψ-nan (TV)          | 8.29   |
| Fairy Tail (2014)                  | 8.25   |
| Fairy Tail                         | 8.22   |
| D.Gray-man                         | 8.20   |
| Kodomo no Omocha (TV)              | 8.18   |
| Dragon Ball                        | 8.16   |
| Touch                              | 8.16   |
| Eyeshield 21                       | 8.08   |
| Prince of Tennis                   | 8.04   |
| Saint Seiya                        | 8.03   |
| Hokuto no Ken                      | 7.99   |
| Kindaichi Shounen no Jikenbo (TV)  | 7.96   |
| Bleach                             | 7.95   |

<br>

  - **Anime Popularity Distribution**
  ![output](https://github.com/user-attachments/assets/9a4e2e22-261d-4f18-80f8-413ba1ac66ec)

_There are anime with very big popularity and famous. Popularity value that exceeds 50000 is anime with big popularity. And the average for overall anime popularity is around ~18000_

  - **Rating Distribution**
    ![output](https://github.com/user-attachments/assets/1b427dcc-79f5-4c8f-9bfc-d488f1396a6c)

_On average, anime is rated 7 - 8_
<br> <br>

  - **Episodes Distribution**
    ![output](https://github.com/user-attachments/assets/e1296f91-016a-48f8-8d63-c94761947892)

_Overall, the average anime episode is 12 episodes. There are also anime with more than 100 episodes and even more than 1000 episodes_
<br> <br>

### 2. Bivariate Analysis

  - **Relationship Popularity and Rating**
![output](https://github.com/user-attachments/assets/1bc523ab-9561-4d3c-a668-6f25b432b8bf)

_The relationship between anime ratings and popularity tends to be stuck at a rating of 8. The greater the popularity, the closer the rating value is to 8._

<br><br>

  - **Boxplot Rating for each Category/Type**
   ![output](https://github.com/user-attachments/assets/000b4290-7101-4712-9451-9864b5d27da7)

   _box plot with the highest average rating, namely the TV category_  <br> <br>
    

  - **Correlation Episodes and Rating**
    ![output](https://github.com/user-attachments/assets/39db0582-514a-43fd-a0ff-6052817ee3a2)

    _The correlation tends to stagnate for episodes approaching/more than 500 episodes, the rating is at 8_

  - **Distribution Anime Episodes Between Each Type/Category**
    ![output](https://github.com/user-attachments/assets/f1153b5c-eebd-4149-adc3-34c686558b75)

    | type    | episodes   |
    |---------|------------|
    | Movie   | 1.095486   |
    | Music   | 1.129098   |
    | ONA     | 6.425954   |
    | OVA     | 2.381571   |
    | Special | 2.555556   |
    | TV      | 34.011914  |

_TV category is an anime with the most episodes among others_  <br> <br>


## Data Preparation

<br>

**Tahap-Tahap Data Preparation yg dilakukan :**
1. **Menghapus Missing/Values** <br>
*Alasannya : Supaya Data menjadi bersih dan bisa dilatih oleh Model. Karena Neural Network tidak bisa menangani Missing Values, oleh karena itu Kita harus menghapus nya terlebih dahulu*
```<class 'pandas.core.frame.DataFrame'>
RangeIndex: 12294 entries, 0 to 12293
Data columns (total 7 columns):
 #   Column    Non-Null Count  Dtype  
---  ------    --------------  -----  
 0   anime_id  12294 non-null  int64  
 1   name      12294 non-null  object 
 2   genre     12232 non-null  object 
 3   type      12269 non-null  object 
 4   episodes  12294 non-null  object 
 5   rating    12064 non-null  float64
 6   members   12294 non-null  int64  
dtypes: float64(1), int64(2), object(4)
memory usage: 672.5+ KB
```
<br> <br>
3. **Menghapus Duplikat data** <br>

*Alasannya : Untuk menghindari Bias yg terjadi*
```Duplicated data from Anime data : 0
Duplicated data from User data : 1
```
<br> <br>
4. **Mengubah Tipe data kolom dari Object menjadi Number** <br>
*Alasannya : Supaya data bisa diproses dan dilatih oleh model sesuai nilainya.*
```<class 'pandas.core.frame.DataFrame'>
RangeIndex: 12208 entries, 0 to 12207
Data columns (total 7 columns):
 #   Column    Non-Null Count  Dtype  
---  ------    --------------  -----  
 0   anime_id  12208 non-null  int64  
 1   name      12208 non-null  object 
 2   genre     12208 non-null  object 
 3   type      12208 non-null  object 
 4   episodes  12208 non-null  object 
 5   rating    12208 non-null  float64
 6   members   12208 non-null  int64  
dtypes: float64(1), int64(2), object(4)
memory usage: 667.8+ KB
```
<br> <br>

5. **Label Encoding untuk Mengubah fitur Kategorial Menjadi Numerik pada kolom Genre dan Type** <br>
   *After Label Encoding :*
   
| user_id | anime_id | user_rating | name                    | genre                                              | type | episodes | anime_rating | members   | genre_list                                     | type_encoded | genre_encoded               |
|---------|----------|-------------|-------------------------|---------------------------------------------------|------|----------|--------------|-----------|-----------------------------------------------|--------------|-----------------------------|
| 1       | 20       | -1          | Naruto                 | Action, Comedy, Martial Arts, Shounen, Super P...| TV   | 220.0    | 7.81         | 683297.0  | [Action, Comedy, Martial Arts, Shounen, Super ... | 5            | [1, 4, 18, 33, 38]          |
| 1       | 24       | -1          | School Rumble          | Comedy, Romance, School, Shounen                  | TV   | 26.0     | 8.06         | 178553.0  | [Comedy, Romance, School, Shounen]              | 5            | [4, 26, 28, 33]             |
| 1       | 79       | -1          | Shuffle!               | Comedy, Drama, Ecchi, Fantasy, Harem, Magic, R...| TV   | 24.0     | 7.31         | 158772.0  | [Comedy, Drama, Ecchi, Fantasy, Harem, Magic, ... | 5            | [4, 7, 8, 9, 11, 17, 26, 28, 30] |
| 1       | 226      | -1          | Elfen Lied             | Action, Drama, Horror, Psychological, Romance,...| TV   | 13.0     | 7.85         | 623511.0  | [Action, Drama, Horror, Psychological, Romance...| 5            | [1, 7, 14, 25, 26, 30, 39]  |
| 1       | 241      | -1          | Girls Bravo: First Season | Comedy, Ecchi, Fantasy, Harem, Romance, School | TV   | 11.0     | 6.69         | 84395.0   | [Comedy, Ecchi, Fantasy, Harem, Romance, School]| 5            | [4, 8, 9, 11, 26, 28]       |

_`genre_list` dan `type_encoded` merupakan data kategorial yg sudah di encoded_

6. **Split dataset menjadi Train and Test data**  <br>
   *Alasannya : Karena supaya bisa mengevaluasi sebuah model dgn data yg belum terlihat sebelumnya.*

   ```Data Type of Train data : <class 'numpy.ndarray'>
   Data Type of Test data : <class 'numpy.ndarray'>
   Train data shape : (5703429,)
   Test data shape : (633715,)
   ```

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Teknik Sistem Rekomendasi yg digunakan :**
  1. **Hybrid Recommendation (Gabungan Collaborative Filtering + Content-Based Filtering)**
  2. **Neural Collaborative Filtering (NCF)**
<br>

### 1. Hybrid Recommendation
<br> <br>

**A. Collaborative Filtering**
  ![1_QuK-dyK7j8equezsRYZ9hQ](https://github.com/user-attachments/assets/c3c9ebf1-d4c9-4a5b-9d99-500fedb47950)

  _Collaborative Filtering berbasis Matrix Factorization adalah Teknik dalam sistem rekomendasi yg bekerja dgn melakukan dot product antara data user dgn data item untuk mencari interaksi antar keduanya._ <br> <br>
  **Macam-macam Matrix Factorization : <br>
    1. Alternating Least Squares (ALS) <br>
    2. Singular Value Decomposition (SVD) <br>
    3. Non-Negative Matrix Factorization (NMF) <br>
    4. Probabilistic Matrix Factorization (PMF) <br>
    5. Matrix Factorization w SGD**  <br>

  - Dalam Teknik **Collaborative Filtering**, saya menggunakan Metode **Matrix Factorization** yaitu menggunakan Algoritma **SVD (Singular Value Decomposition)** untuk mencari interaksi antara user dan anime dan mencari kesamaan dari user tsb. <br>

  - Setelah dibuat modelnya , misalkan seorang user 1 menyukai Anime ini :
    
| user_id | anime_id | user_rating | name                  | genre                                     | type | episodes | anime_rating | members   |
|---------|----------|-------------|-----------------------|-------------------------------------------|------|----------|--------------|-----------|
| 1       | 8074     | 10          | Highschool of the Dead | Action, Ecchi, Horror, Supernatural       | TV   | 12       | 7.46         | 535892.0  |
| 1       | 11617    | 10          | High School DxD       | Comedy, Demons, Ecchi, Harem, Romance, School | TV   | 12       | 7.70         | 398660.0  |
| 1       | 11757    | 10          | Sword Art Online      | Action, Adventure, Fantasy, Game, Romance | TV   | 25       | 7.83         | 893100.0  |
| 1       | 15451    | 10          | High School DxD New   | Action, Comedy, Demons, Ecchi, Harem, Romance,...| TV   | 12       | 7.87         | 266657.0  |

**Maka 10 Top rekomendasi anime terbaik untuk user 1 adalah :** 
| anime_id | name                              | genre                                     | type   | episodes | rating | members  | genre_preprocessed                       | predicted_rating |
|----------|-----------------------------------|-------------------------------------------|--------|----------|--------|----------|-------------------------------------------|------------------|
| 2904     | Code Geass: Hangyaku no Lelouch R2 | Action, Drama, Mecha, Military, Sci-Fi, Super ... | TV     | 25       | 8.98   | 572888   | Action, Drama, Mecha, Military, Sci-Fi, Super_... | 9.866580        |
| 226      | Elfen Lied                        | Action, Drama, Horror, Psychological, Romance,... | TV     | 13       | 7.85   | 623511   | Action, Drama, Horror, Psychological, Romance,... | 9.783011        |
| 6702     | Fairy Tail                        | Action, Adventure, Comedy, Fantasy, Magic, Sho... | TV     | 175      | 8.22   | 584590   | Action, Adventure, Comedy, Fantasy, Magic, Sho... | 9.757270        |
| 1575     | Code Geass: Hangyaku no Lelouch   | Action, Mecha, Military, School, Sci-Fi, Super... | TV     | 25       | 8.83   | 715151   | Action, Mecha, Military, School, Sci-Fi, Super... | 9.754623        |
| 10620    | Mirai Nikki (TV)                  | Action, Mystery, Psychological, Shounen, Super... | TV     | 26       | 8.07   | 657190   | Action, Mystery, Psychological, Shounen, Super... | 9.733267        |
| 731      | Interstella5555: The 5tory of The 5ecret 5tar ... | Adventure, Drama, Music, Sci-Fi             | Music  | 1        | 8.17   | 31464    | Adventure, Drama, Music, Sci-Fi             | 9.638481        |
| 16894    | Kuroko no Basket 2nd Season       | Comedy, School, Shounen, Sports            | TV     | 25       | 8.58   | 243325   | Comedy, School, Shounen, Sports            | 9.630045        |
| 317      | Final Fantasy VII: Advent Children | Action, Fantasy, Super Power                | Movie  | 1        | 7.94   | 138659   | Action, Fantasy, Super_Power                | 9.626753        |
| 22319    | Tokyo Ghoul                      | Action, Drama, Horror, Mystery, Psychological,... | TV     | 12       | 8.07   | 618056   | Action, Drama, Horror, Mystery, Psychological,... | 9.595076        |
| 1699     | Romeo x Juliet                   | Drama, Fantasy, Historical, Romance         | TV     | 24       | 7.85   | 91530    | Drama, Fantasy, Historical, Romance         | 9.593245        |

<br>
----------------------------------------------------------------------------------------

**B. Content-Based Filtering**
    ![content-based-recommendation-system-1024x576](https://github.com/user-attachments/assets/234803a9-ffcd-49d9-961b-36d75aa55340)

  _Content-Based Filtering yaitu teknik dalam sistem rekomendasi yg merekomendasikan sebuah item/produk berdasarkan data history seorang pengguna. misalkan jika pengguna menyukai item A , maka sistem akan merekomendasikan item yg mirip dgn item A ke pengguna._
  - Dalam Teknik **Content-Based Filtering**, saya menggunakan Rumus **Cosine Similarity** untuk mencari Kesamaan/kemiripan antara anime-anime berdasarkan fitur `genre`, `type`, `episodes`, `rating`. bisa juga selain itu menggunakan Rumus **Correlation Pearson** untuk mencari korelasi antar anime tsb <br>
     ok sekarang kita akan memprediksi hasilnya. misalkan jika user 1 menyukai anime ini :
    
| user_id | anime_id | user_rating | name                  | genre                                     | type | episodes | anime_rating | members   |
|---------|----------|-------------|-----------------------|-------------------------------------------|------|----------|--------------|-----------|
| 1       | 8074     | 10          | Highschool of the Dead | Action, Ecchi, Horror, Supernatural       | TV   | 12       | 7.46         | 535892.0  |
| 1       | 11617    | 10          | High School DxD       | Comedy, Demons, Ecchi, Harem, Romance, School | TV   | 12       | 7.70         | 398660.0  |
| 1       | 11757    | 10          | Sword Art Online      | Action, Adventure, Fantasy, Game, Romance | TV   | 25       | 7.83         | 893100.0  |
| 1       | 15451    | 10          | High School DxD New   | Action, Comedy, Demons, Ecchi, Harem, Romance,...| TV   | 12       | 7.87         | 266657.0  |

<br> <br> **Maka top 10 rekomendasi anime terbaik untuk user 1 adalah :** <br> <br>

**Kelebihan :**

1. Menggabungkan CBF + CF yg bisa memprediksi hasil prediksi yg lebih baik.
2. Hybrid Recommendation bisa menangani **Cold Start, Sparsity, dan Diversity** dalam rekomendasi

**Kelemahan :**
1. Hybrid Recommendation membutuhkan kompleksitas yg tinggi dan waktu pelatihan yg lama dalam melatih data.
2. Kinerja nya bias lebih lambat dibanding Teknik dasarnya (yaitu CBF / CF)
<br> <br>

| anime_id | name                                | genre                                     | type    | episodes | rating | members  | genre_preprocessed                       | type_encoded | genre_encoded               | predicted_rating |
|----------|-------------------------------------|-------------------------------------------|---------|----------|--------|----------|-------------------------------------------|--------------|-----------------------------|------------------|
|          | Fairy Tail                         | Action, Adventure, Comedy, Fantasy, Magic, Sho...| TV      | 175      | 8.22   | 584590   | [Action, Adventure, Comedy, Fantasy, Magic, Sho...| 5            | [1, 2, 4, 9, 17, 33]       | 9.977149         |
| 32281    | Kimi no Na wa.                     | Drama, Romance, School, Supernatural      | Movie   | 1        | 9.37   | 200630   | [Drama, Romance, School, Supernatural]      | 0            | [7, 26, 28, 39]             | 9.974690         |
| 28851    | Koe no Katachi                     | Drama, School, Shounen                    | Movie   | 1        | 9.05   | 102733   | [Drama, School, Shounen]                    | 0            | [7, 28, 33]                 | 9.968632         |
| 22043    | Fairy Tail (2014)                  | Action, Adventure, Comedy, Fantasy, Magic, Sho...| TV      | 102      | 8.25   | 255076   | [Action, Adventure, Comedy, Fantasy, Magic, Sho...| 5            | [1, 2, 4, 9, 17, 33]       | 9.963638         |
| 30654    | Ansatsu Kyoushitsu (TV) 2nd Season | Action, Comedy, School, Shounen           | TV      | 25       | 8.68   | 176475   | [Action, Comedy, School, Shounen]           | 5            | [1, 4, 28, 33]              | 9.958812         |
| 28977    | Gintama°                          | Action, Comedy, Historical, Parody, Samurai, S...| TV      | 51       | 9.25   | 114262   | [Action, Comedy, Historical, Parody, Samurai, ... | 5            | [1, 4, 13, 23, 27, 29, 33] | 9.949050         |
| 24703    | High School DxD BorN               | Action, Comedy, Demons, Ecchi, Harem, Romance,...| TV      | 12       | 7.71   | 192171   | [Action, Comedy, Demons, Ecchi, Harem, Romance...| 5            | [1, 4, 6, 8, 11, 26, 28]   | 9.942084         |
| 32935    | Haikyuu!!: Karasuno Koukou VS Shiratorizawa Ga... | Comedy, Drama, School, Shounen, Sports   | TV      | 10       | 9.15   | 93351    | [Comedy, Drama, School, Shounen, Sports]   | 5            | [4, 7, 28, 33, 37]          | 9.941214         |
| 1479     | City Hunter: Kinkyuu Namachuukei!? Kyouakuhan ... | Shounen                                 | Special | 1        | 7.60   | 2506     | [Shounen]                                 | 4            | [33]                        | 9.940308         |
| 4155     | One Piece Film: Strong World       |                                           |         |          |        |          |                                           |              |                             |                  |

    
**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
