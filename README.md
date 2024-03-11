# Termux-dekstop

### Transformasi Ponsel Android Menjadi Desktop Linux

#### **Pendahuluan:**
Ingin lebih banyak hal dengan ponsel Anda, seperti menyiapkan server web atau server Node.js, dan menjalankan aplikasi web langsung di ponsel Anda? Dengan Termux, Anda dapat menjalankan desktop Linux lengkap di perangkat Android Anda. Berikut adalah panduan langkah-demi-langkah untuk mengatur Termux dengan lingkungan desktop, khususnya XFCE, pada ponsel Anda.

#### **Apa Itu Termux?**
Termux adalah aplikasi Android yang meniru shell Linux, tidak memerlukan hak akses root, dan sepenuhnya gratis. Artikel ini memberikan panduan langkah-demi-langkah tentang cara mengatur Termux pada perangkat Android Anda.

#### **Prasyarat:**
- Perangkat Android minimal versi 7 atau Fire OS 6.

#### **Instalasi:**
1. **Unduh F-Droid:**
   - [Link F-Droid APK](https://f-droid.org/FDroid.apk)
2. **Instal F-Droid:**
   - Izinkan instalasi dari sumber luar Play Store.
   ```sh
   pkg install /path/to/FDroid.apk
   ```

#### **Konfigurasi Dasar:**
1. **Perbarui Manajer Paket:**
   ```sh
   pkg upgrade
   ```
2. **Set Up Penyimpanan:**
   ```sh
   termux-setup-storage
   ```
3. **Konfigurasi Tombol Tambahan:**
   ```sh
   nano ~/.termux/termux.properties
   termux-reload-settings
   ```

#### **Menggunakan Manajer Paket:**
- **Cari Paket:**
  ```sh
  pkg search <query>
  ```
- **Instal Paket:**
  ```sh
  pkg install <package-name>
  ```
- **Perbarui Semua Paket:**
  ```sh
  pkg upgrade
  ```
- **Hapus Paket:**
  ```sh
  pkg uninstall <package-name>
  ```

#### **Setting Up Desktop Environment (XFCE):**
1. **Aktifkan Repositori x11:**
   ```sh
   pkg install x11-repo
   ```
2. **Instal VNC Server:**
   ```sh
   pkg install tigervnc
   ```
3. **Mulai VNC Server pada localhost:**
   ```sh
   vncserver -localhost
   ```
4. **Setel Variabel Lingkungan untuk Display:**
   ```sh
   echo 'export DISPLAY=":1"' >> ~/.bashrc
   . ~/.bashrc
   ```
5. **Instal Desktop Environment XFCE:**
   ```sh
   pkg install xfce4
   ```
6. **Konfigurasi Startup XFCE untuk VNC:**
   ```sh
   nano .vnc/xstartup
   ```
   - Hapus atau komentar semua yang ada, gantilah dengan:
     ```sh
     #!/data/data/com.termux/files/usr/bin/sh
     xfce4-session &
     ```
7. **Instal Browser dan Terminal (Opsional):**
   ```sh
   pkg install firefox xfce4-terminal
   ```

#### **Kesimpulan:**
Sekarang, ponsel Android Anda dapat menjalankan desktop Linux dengan XFCE. Unduh RealVNC Viewer dari Play Store, tambahkan koneksi baru dengan alamat "localhost:5901", dan nikmati desktop Linux di ponsel Anda.
