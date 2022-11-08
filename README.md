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
    - FloatingActionButton _> FloatingActionButtons adalah widget yang  berfungsi untuk menambahkan tombol yang dapat di klik yang biasanya melayang pada layar aplikasi.

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

    


