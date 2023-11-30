# git-server-tutorial

step by step membuat suatu git server :
1. membuat suatu user git (contoh nama user = git)
```bash
$ sudo adduser git
```

2. membuat folder .ssh dan file authorized_keys di user yang baru kita buat untuk menginput ssh-key client
```bash
$ su git
$ mkdir .ssh && chmod 700 .ssh
$ touch .ssh/athorized_keys && chmod 600 .ssh/authorized_keys
```

3. Menginput ssh-key client yang dapat mengakses git server kita
```bash
$ vi authorized_keys
```

4. keluar dari user git, lalu buatlah suatu directory pada local yang mana nantinya akan dijadikan base server directory untuk git server kita
```bash
$ cd /home/eros/uji-coba
$ mkdir git
$ chown git:git git
$ cd git
```

5. Masuk kembali ke user git kita
```bash
$ su git
$ cd /home/eros/uji-coba/git 
```

6. Buat folder untuk menyimpan file server kita dan konfigurasikan ke git
```bash
$ mkdir files.git
$ cd files.git
$ git init --bare
```

7. Uji coba di PC client apakah sudah bisa mengakses git server atau belum dengan cara mengclone isi dari server kita
```bash
$ git clone git@(ip pc server):/home/eros/git/files.git
```

8. Apabila kita ingin mem-push ke server, maka lalukan langkah-langkah push standar seperti pada github yang mana branch untuk git server ini sendiri yaitu master
