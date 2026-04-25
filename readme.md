ZMK Totem Seeed Studio XIAO BLE Wireless.
[ZMK STUDIO](https://zmk.studio/)
Ada update baru ZMK Studio remapping tanpa perlu di flash 

[Full Dokumentasi ZMK](https://zmk.dev/docs)


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
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="/docs/images/TOTEM_logo_dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="/docs/images/TOTEM_logo_bright.svg">
  <img alt="TOTEM logo font" src="/docs/images/TOTEM_logo_bright.svg">
</picture>

# ZMK CONFIG FOR THE TOTEM SPLIT KEYBOARD

[Here](https://github.com/GEIGEIGEIST/totem) you can find the hardware files and build guide.\
[Here](https://github.com/GEIGEIGEIST/qmk-config-totem) you can find the QMK config for the TOTEM.

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
