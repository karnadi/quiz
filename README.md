# EnixApp - Quiz

Cuma template javascript yang dibangun menggunakan [VueJS](https://vuejs.org) dan framework/library lainnya:

1. [AlaSQL](https://alasql.org) (local storage database)
2. [ShowdownJS](https://showdownjs.com) (markdown)
3. [Date-FNS](https://date-fns.org)
4. [Bootstrap-v4](https://getbootstrap.com)
5. [Bootstrap-Vue](https://bootstrap-vue.org)
6. [Bootswatch Theme](https://bootswatch.com) (alternatif Bootstrap tema)
7. [Lodash](https://lodash.org)
8. De el el

Tipe soal yang didukung:

1. Pilihan Ganda (PG).
2. Multi Jawaban (MJ).
3. Benar/Salah (BS).
4. Isian (IS) untuk jawaban singkat.
5. Esai (ES) untuk jawaban terperinci.

## Skema JSON

```json
{
	"soal_1": {},
	"soal_2": {},
	"soal_3": {},
	"soal_<n>": {}
}
```

Penomoran di atas **wajib** berurutan.

## Contoh skema dengan Opsi Pilihan

Contoh skema bisa dilihat di direktori **assets**.

### Contoh untuk soal Pilihan Ganda (PG):

```json
{
  "soal_1": {
    "tipe": "pg",
    "body": "Pemain sepakbola yang pernah membela klub Real Madrid di antaranya....",
    "opsi": {
      "column": 2,
      "items": {
        "opsi_1": {
          "body": "Cristiano Ronaldo"
        },
        "opsi_2": {
          "body": "Santiago Solari"
        },
        "opsi_3": {
          "body": "Luis Suarez"
        }
      }
    }
  }
}
```

Minimal opsi jawaban untuk tipe soal Pilihan Ganda (PG) adalah 3 (tiga).

### Contoh untuk soal Multi Jawaban (MJ): 

```json
{
  "soal_1": {
    "tipe": "mj",
    "body": "Pemain sepakbola yang pernah membela klub Real Madrid di antaranya....",
    "opsi": {
      "column": 2,
      "items": {
        "opsi_1": {
          "body": "Cristiano Ronaldo"
        },
        "opsi_2": {
          "body": "Santiago Solari"
        },
        "opsi_3": {
          "body": "Luis Suarez"
        }
      }
    }
  }
}
```

Minimal opsi jawaban untuk tipe soal Multi Jawaban (MJ) adalah 3 (tiga).

### Contoh untuk soal Benar/Salah (BS): 

```json
{
  "tipe": "bs",
  "body": "Pemain sepakbola *Cristiano Ronaldo* pernah membela <em>Manchester United</em>.",
  "opsi": {
    "column": 2
  }
}
```

Minimal opsi jawaban untuk tipe soal Benar/Salah (BS) adalah 2 (dua).

### Contoh untuk soal Isian (IS) dan Esai (ES): 

```json
{
  "soal_4": {
    "tipe": "is",
    "body": "Jumlah Trofi Liga Champions yang dimenangkan Real Madrid saat ini berjumlah....",
  },
  "soal_5": {
    "tipe": "es",
    "body": "Sebutkan 5 pemain yang membela Real Madrid pada musim 2018/2019.",
  }
}
```

### Kolom Opsi Jawaban

Untuk kolom opsi jawaban hanya bernilai 1 atau 2 (number/integer), opsional (default: 1).

```json
{
  "tipe": "pg",
  "body": "Pemain sepakbola *Cristiano Ronaldo* pernah membela <em>Manchester United</em>.",
  "opsi": {
    "column": 2
  }
}
```

## Konfigurasi

```js
  window.EnixApp = {
    quiz: {
      baseUri: "/quiz/",
      source: "/quiz/assets/quiz_data.json",
      duration: 5, // seconds
      interval: 60, // seconds
      onInterval: function(data) {
        // console.log(data)
        // kirim data server setiap 60 detik
        // lihat pengaturan `interval`
        // console.info('Menyimpan data ke server.', new Date())
      },
      onFinish: function(data) {
        // console.warn('Waktu habis!', new Date())
      }
    }
  }
```

contoh URL untuk pengaturan di atas:

```
http://example.com/quiz
```

## TODO

1. Tampilan log aktivitas.
2. Tabel data.
3. Konfigurasi waktu mulai dengan format *00:00:00*.
