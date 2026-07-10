ZMK Totem Seeed Studio XIAO BLE Wireless.
[ZMK STUDIO](https://zmk.studio/)
Ada update baru ZMK Studio remapping tanpa perlu di flash 

[Full Dokumentasi ZMK](https://zmk.dev/docs)

NOTES !!!

Saat charging harus dalam keadaan ON (slider di slide sebelah kiri). fungsi slider memutuskan arus dari baterai ke MCU. Jadi saat charge posisi slider harus on


Tools :
[ZMK Keymap Editor](https://nickcoutsos.github.io/keymap-editor/)
Video fork repository :
[Tutorial Mapping ZMK](https://youtu.be/cAi5pnkz48M)


Prosedur Reset Keyboard Split
Lakukan langkah-langkah berikut untuk mereset semua bagian keyboard split Anda:
- Masukkan setiap bagian keyboard split ke mode bootloader. Dengan cara tekan 2x tombol reset saat USB terhubung akan muncul drive baru, untuk flash nya cukup drag & drop di disk bootloader
- Flash salah satu bagian keyboard dengan firmware reset pengaturan setting_reset.uf2.
- Ulangi langkah 2 pada bagian lainnya dari keyboard split.
- Flash image firmware yang sebenarnya untuk setiap bagian keyboard split (misalnya my_board_left.uf2 untuk bagian kiri, my_board_right.uf2 untuk bagian kanan).
- Jika central dan peripheral tidak saling terhubung setelah menyelesaikan langkah-langkah ini, akan membantu untuk mereset central dan peripheral pada waktu yang hampir bersamaan. Biasanya dilakukan dengan menghubungkan pin reset ke ground pada setiap mikrokontroler keyboard Anda, menekan tombol reset, atau mematikan lalu menyalakan keduanya dengan sakelar daya.
- Setelah selesai, Anda harus menghapus/lupakan keyboard dari perangkat host mana pun yang sebelumnya terpasang, lalu lakukan pairing ulang, karena informasi pairing tersebut juga telah dihapus dari keyboard.



# Panduan Bluetooth ZMK (Keyboard Tanpa Layar)

Keyboard ZMK memiliki beberapa slot Bluetooth yang bekerja seperti **beberapa "tempat parkir" untuk perangkat**. Meskipun keyboard tidak memiliki layar, sistem ini tetap bekerja dengan cara yang sama.

### 📌 1. Slot Bluetooth

Bayangkan keyboard memiliki beberapa tempat parkir.

* **BT_SEL 0** = Slot 1
* **BT_SEL 1** = Slot 2
* **BT_SEL 2** = Slot 3
* dan seterusnya.

Setiap slot hanya dapat menyimpan **satu perangkat**.

Contoh:

* Slot 1 → PC
* Slot 2 → Tablet
* Slot 3 → MacBook

Saat ingin berpindah perangkat, cukup tekan tombol **BT_SEL** yang sesuai dengan slot perangkat tersebut.

---

### 📌 2. Jika Keyboard Tidak Terhubung

Karena keyboard tidak memiliki layar, Anda tidak akan melihat status koneksi.

Apabila keyboard tidak dapat terhubung, kemungkinan:

* Perangkat tujuan sedang mati.
* Bluetooth perangkat sedang nonaktif.
* Slot tersebut belum pernah dipasangkan (pairing).
* Slot masih menyimpan perangkat lama.

---

### 📌 3. Pairing Ulang

Jika ingin memasangkan perangkat baru pada slot yang sedang digunakan:

1. Pilih slot dengan **BT_SEL**.
2. Tekan **BT_CLR** untuk menghapus data Bluetooth pada slot tersebut.
3. Masuk ke menu Bluetooth di PC/HP/Tablet.
4. Cari nama keyboard, lalu lakukan pairing.

Setelah berhasil, perangkat baru akan tersimpan pada slot tersebut.

---

### 📌 4. Slot Tidak Bisa Langsung Diganti

Slot Bluetooth tidak dapat langsung diisi perangkat baru.

Misalnya:

* Slot 1 sebelumnya tersimpan untuk Laptop A.
* Anda ingin menggunakan Slot 1 untuk Laptop B.

Maka Anda harus:

* Menghapus Slot 1 menggunakan **BT_CLR**, atau
* Menggunakan slot lain yang masih kosong.

---

### 📌 5. Contoh Penggunaan

Agar lebih praktis, gunakan pembagian seperti berikut:

* **BT_SEL 0** → PC
* **BT_SEL 1** → Tablet
* **BT_SEL 2** → MacBook
* **BT_SEL 3** → Smartphone

Dengan begitu, Anda cukup menekan tombol **BT_SEL** sesuai perangkat yang ingin digunakan, tanpa perlu melakukan pairing setiap kali berpindah perangkat.










<picture>
  <source media="(prefers-color-scheme: dark)" srcset="/docs/images/TOTEM_logo_dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="/docs/images/TOTEM_logo_bright.svg">
  <img alt="TOTEM logo font" src="/docs/images/TOTEM_logo_bright.svg">
</picture>

# ZMK CONFIG FOR THE TOTEM SPLIT KEYBOARD


TOTEM is a 38 key column-staggered split keyboard running [ZMK](https://zmk.dev/) or [QMK](https://docs.qmk.fm/). It's meant to be used with a SEEED XIAO BLE or RP2040.


![TOTEM layout](/docs/images/TOTEM_layout.svg)



## HOW TO USE

- fork this repo
- `git clone` your repo, to create a local copy on your PC (you can use the [command line](https://www.atlassian.com/git/tutorials) or [github desktop](https://desktop.github.com/))
- adjust the totem.keymap file (find all the keycodes on [the zmk docs pages](https://zmk.dev/docs/codes/))
- `git push` your repo to your fork
- on the GitHub page of your fork navigate to "Actions"
- scroll down and unzip the `firmware.zip` archive that contains the latest firmware
- connect the left half of the TOTEM to your PC, press reset twice
- the keyboard should now appear as a mass storage device
- drag'n'drop the `totem_left-seeeduino_xiao_ble-zmk.uf2` file from the archive onto the storage device
- repeat this process with the right half and the `totem_right-seeeduino_xiao_ble-zmk.uf2` file.
