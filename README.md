 # Docker - Orkestrasi menggunakan Docker Compose

 ### 1. MENENTUKAN KONTAINER PERTAMA
Dasar dari docker compose adalah terletak pada file docker-compose.yml . 
Dalam skenari ini memiliki aplikasi Node.js yang memerlukan koneksi redis. Untuk memulai, kita harus mendefinisikan file docker-compose.yml 
terlebih dahulu. Format file ini didasarkan pada YAML (Yet Another Markup Language).
berikut adalah format file docker-compose.yml :
   ![1](https://github.com/ayuwidyainggit/docker-ayu/blob/master/images/1.PNG)
   
yaml tersebut akan menentukan container yang disebut web.

 ### 2. MENENTUKAN PENGATURAN 
Docker Compose mendukung semua properti yang dapat didefinisikan menggunakan docker run.
Untuk menghubungkan dua container bersama untuk menentukan link properti  dan mendaftar koneksi yang diperlukan menggunakan source code seperti di bawah ini :

   ![2](https://github.com/ayuwidyainggit/docker-ayu/blob/master/images/2.PNG)
	 
 ### 3. MENDEFINISIKAN KONTAINER KE DUA 
Pada langkah sebelumnya adalah menggunakan Dockerfile di direktori yang saat ini sebagai basis untuk containernya. 
Untuk mendefinisikan kontainer ke dua caranya adalah dengan menggunakan image yang ada dari Docker Hub sebagai container kedua.
Mendefinisikan container ke dua dengan nama redis dan menggunkan image redis. Format YAML nya adalah seperti di bawah ini :
     ![3](https://github.com/ayuwidyainggit/docker-ayu/blob/master/images/3.PNG)
 ### 4. DOCKER UP
Setelah membuat file docker-compose.yml maka kita dapat menggunakan aplikasi yang kita punya dengan perintah single command of up.
Jika ingin memunculkan satu kontainer saja maka menggunakan perintah dengan format <name>
Perintah -d digunakan untuk menjalankan kontainer di background, sama seperti saat menggunakan docker run.
Untuk run aplikasi menggunakan perintah docker compose up -d  pada cmd.
     ![4](https://github.com/ayuwidyainggit/docker-ayu/blob/master/images/4.PNG)
	  
 ### 5. MANAGEMEN DOCKER 
Docker compose tidak hanya mengelola satu container saja tetapi dapat mengelola semua kontainer hanya menggunakan satu perintah saja. 
Perintahnya adalah docker-compose ps
    Hasilnya :
     ![5](https://github.com/ayuwidyainggit/docker-ayu/blob/master/images/5.PNG)
Perintah untuk mengelola semua log
 docker-compose logs 
     ![6](https://github.com/ayuwidyainggit/docker-ayu/blob/master/images/6.PNG)

Perintah lain untuk run banyak kontainer dengan docker 
 docker-compose
     ![7](https://github.com/ayuwidyainggit/docker-ayu/blob/master/images/7.PNG)
 
 ### 6. SKALA DOCKER
Selain dapat me run container aplikasi, docker compose juga dapat mengukur jumlah kontainer yang sedang dijalankan.
Opsi skala digunakan untuk menentukan layanan dan kemudian jumlah instance yang inginkan. 
Jika angkanya lebih besar dari instans yang sudah berjalan, maka akan meluncurkan container tambahan. 
Namun jika jumlahnya kurang, maka itu akan menghentikan container yang tidak diminta.
untuk mengetahui skala container web yang dijalankan maka menggunakan perintah :
docker-compose scale web=3
hasil:
    ![8](https://github.com/ayuwidyainggit/docker-ayu/blob/master/images/8.PNG)
dalam perintah ini karena kontainer hanya ada satu, dan perintah tersebut skalanya 3 maka akan membuat container tambahan yaitu tutorial_web_2 dan tutorial_web_3.

jika inging menurunkan menggunakan perintah 
docker-compose scale web=1
    ![9](https://github.com/ayuwidyainggit/docker-ayu/blob/master/images/9.PNG)
dalam perintah ini tutorial_web_2 dan tutorial_web_3 dihentikan karena jumlah yang diinginkan hanya 1.

 ### 7. MENGHENTIKAN Docker
Untuk menghentikan container menggunakan perintah 
docker-compose stop
hasil :
    ![10](https://github.com/ayuwidyainggit/docker-ayu/blob/master/images/10.PNG)
 container tutorial_web_1 dan tutorial_redis_1 dihentikan
 
untuk menghapus semua kontainer menggunakan	docker-compose rm
