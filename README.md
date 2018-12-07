 # Docker Compose 
 
 aplikasi yang komponennya lebih dari satu.
 kalau service lebih dari satu maka harus disatukan dengan docker container
 
 1. Defining First Container
 web:
  build: .

  2. Defining Settings
  Untuk menghubungkan dua kontainer bersama-sama untuk menentukan properti tautan dan mencantumkan koneksi yang diperlukan. 
  Misalnya, yang berikut ini akan menautkan ke penampung sumber redis yang ditentukan dalam file yang sama dan menetapkan nama yang sama ke alias.
   links:
    - redis
	
	==> redis adalah inmemory database. karena saat menjalankan pertama kali dia mengambil dari memory sehingga prosesnya lebih cepet .
	

	Format yang sama digunakan untuk properti lain seperti port
ports:
    - "3000"
    - "8000"

## 3. Define Second Container
   Tentukan kontainer kedua dengan nama redis yang menggunakan images redis denga format YAML, 
           redis:
           image: redis:alpine
           volumes:
           - /var/redis/data:/data
	
## Step 4 - Docker Up
Dengan dibuatnya file docker-compose.yml, Anda dapat meluncurkan semua aplikasi dengan satu perintah ke atas. Jika Anda ingin memunculkan satu kontainer, maka Anda dapat menggunakan <nama>.
   web:
     build: .

     links:
       - redis

     ports:
       - "3000"
       - "8000"

   redis:
     image: redis:alpine
     volumes:
     - /var/redis/data:/data


Argumen -d menyatakan untuk menjalankan kontainer di BACKGROUND, mirip dengan ketika digunakan dengan menjalankan docker run.

 jalankan aplikasi dengan docker-compose up -d
 
# 5. Docker Management
 gunakan perintah:
	docker-compose ps
	
Untuk mengakses semua log melalui single stream yang Anda gunakan
	docker-compose logs
	docker-compose
	
	
# 6. Docker Scale
Opsi skala digunakan untuk menentukan layanan dan kemudian jumlah instance yang diinginkan. 
Jika angkanya lebih besar dari instance yang sudah berjalan, maka akan meluncurkan kontainer tambahan. 
Jika jumlahnya kurang, maka akan menghentikan kontainer yang tidak diinginkan.
perintah:
     docker-compose --scale web=3

# 7. Docker Stop
untuk menghentikan satu set kontainer Anda dapat menggunakan perintah
     docker-compose stop

Untuk menghapus semua kontainer, gunakan perintah
     docker-compose rm