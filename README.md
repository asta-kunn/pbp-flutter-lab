# counter_7

## Jelaskan apa yang dimaksud dengan stateless widget dan stateful widget dan jelaskan perbedaan dari keduanya
    Stateless widget properties nya bersifat immutable. Maksdunya adalah properti hanya dapat berubah ketika kita mengatur instance baru untuk widget tertentu. Jika tidak maka widget tidak akan dapat mengalami perubahan akibat perubahan nilai dari state yang ada selama runtime aplication.

    Stateful widget propertis nya bersifat mutable, artinya properti dapat diubah selama runtime. Hal ini dikarenakan mutable stated disimpan secara terpisah dalam state object. Nilai dari state juga dapat berubah berdasarkan nilai state yang ada selama runtime aplication.  

## Sebutkan widget apa saja yang kamu pakai di proyek kali ini dan jelaskan fungsinya
    - Scaffold -> Scaffold adalah widget yang berfungsi sebagai layout utama dari aplikasi
    - Appbar -> appbar adalah widget yang berfungsi sebagai header dari aplikasi
    - Center -> Center adalah widget yang berfungsi sebagai layout yang mengatur child widget nya ke tengah
    - Row & Column -> row adalah widget yang berisi beberapa widget lainnya secara horizontal, sedangkan column adalah widget yang berisi widget lainnya secara vertikal
    - Text -> text adalah widget yang digunakan untuk menampilkan teks
    - Visibility -> Visibility adalah widget yang digunakan untuk menampilkan widget lainnya jika kondisi tertentu terpenuhi.
    - FloatingActionButton -> FloatingActionButtons adalah widget yang  berfungsi untuk menambahkan tombol yang dapat di klik yang biasanya melayang pada layar aplikasi.
    - Padding -> padding adalah widget yang digunakan untuk memberikan jarak antar widget

## Apa fungsi dari setState()? Jelaskan variabel apa saja yang dapat terdampak dengan fungsi tersebut   
    fungsi dari setState() adalah untuk memberitahu framework Flutter bahwa sesuatu telah berubah di State ini, yang menyebabkan ia untuk menjalankan kembali metode build di bawah sehingga tampilan dapat mencerminkan nilai yang diperbarui. 
    Pada projek kali ini jika kita mengubah _counter tanpa memanggil setState(), maka metode build tidak akan dipanggil lagi, dan jadi tidak akan tampak apa-apa terjadi.

## Jelaskan perbedaan antara const dengan final
    perbedaan const dan final adalah const adalah nilai yang tidak bisa diubah sedangkan final adalah nilai yang bisa diubah. 

## Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas
    1. Membuat fungsi _decrementCounter() untuk mengurangi counter. dengan code sebagai berikut: 
    void _decrementCounter() {
        setState(() {
        // check if counter == 0, if so, do nothing
        if (_counter == 0) {
            return;
        }
        _counter--;
        });
    }

    2. Menambahkan FloatingActionButton, - pada kiri layar dan + pada kanan layar. Kodingannya seperti berikut (+bonus)
    floatingActionButton:
      Padding(
          padding: const EdgeInsets.only(left: 30),
          child: Row(
            mainAxisAlignment: MainAxisAlignment.spaceBetween,
            children: [
              Visibility(
                visible: _counter > 0,
                child: FloatingActionButton(
                  onPressed: _decrementCounter,
                  tooltip: 'Decrement',
                  child: const Icon(Icons.remove),
                ),
              ),
              FloatingActionButton(
                onPressed: _incrementCounter,
                tooltip: 'Increment',
                child: const Icon(Icons.add),
              ),
            ],
          )),

    3. Menambahkan Method Text untuk warna merah pada angka genap dan biru pada angka ganjil. Implementasi code sebagai berikut.
    Text(
        _counter % 2 == 0 ? 'Genap' : 'Ganjil',
        style: TextStyle(
        color: _counter % 2 == 0 ? Colors.red : Colors.blue,
        ),
    ),           
    Text(
        '$_counter',
        style: Theme.of(context).textTheme.headline4,
    ),


# **Tugas 8**

## Perbedaan Navigator.push dan Navigator.pushReplacement

    Navigator.push itu berfungsi untuk menambahkan route baru ke stack navigasi 
    sedangkan Navigator.pushReplacement itu berfungsi untuk mengganti route yang ada di stack navigasi dengan route baru

## Widget yang dipakai dan fungsinya

-   Container: widget yang berfungsi sebagai _container_ untuk menampung widget lainnya
-   Form: widget yang berfungsi untuk membuat form
-   Column: widget yang berfungsi untuk menampung widget lainnya secara vertikal
-   ListTile: row yang menampung teks sebagai leading dan trailing
-   Drawer: widget yang berfungsi untuk membuat _drawer_ di sisi kiri layar (untuk navigasi)

## Jenis event pada Flutter

-   onTap: event yang terjadi ketika widget di tap
-   onPressed: event yang terjadi ketika widget di tekan
-   onChanged: event yang terjadi ketika widget diubah
-   onSaved: event yang terjadi ketika widget disimpan

## Cara kerja Navigator saat mengganti halaman aplikasi

Navigator mengatur stack of route dan menyediakan dua cara untuk mengatur stack of route, yaitu declarative dan imperative. Declarative menggunakan Navigator.pages, sedangkan imperative Navigator.push dan Navigator.pop

## Implementasi checklist
    1. Bikin file drawer.dart untuk drawer nya yang akan digunakan di data_budget, form_budget, dan main 
    dengan cara drawer: const DrawerApp()

    2. Buat form dengan input String judul, int nominal, String jenisBudget dan tanggal sebagai input form

    3. buat class Budget di form_budget 
    class Budget {
      late String judul;
      late int nominal;
      late String jenisBudget;
      late DateTime tanggal;

      Budget(
          {required this.judul, required this.nominal, required this.jenisBudget, required this.tanggal});
    }

    4. Bikin file globals.dart dan buat variabel global budgets yang menampung list dari Budget
    library counter_7.globals;
    import 'package:counter_7/form_budget.dart';

    List<Budget> budgets = [];

    5. dengan menggunakan ListView.builder data yang ada di globals.budgets dapat ditampilkan di data_budget.dart



