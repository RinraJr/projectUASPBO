# Final Project PBO
### Kelompok 6
Anggota : 
1. Saddam Surya Mardiansyah   - 2017051014
2. Bagus Tito Dwi Saputra     - 2057051018
3. Mahesa Yudhistira          - 1917051029
4. Raesha Salsabila           - 1957051006

Pembagian Tugas :
- Mahesa Yudhistira          : Membuat Class Diagram dan ER Diagram sesuai yang ada dalam project
- Raesha Salsabila           : Menginisialisasi dan mengembangkan class yang digunakan dalam project
- Bagus Tito Dwi Saputra     : Membuat dan menghubungkan program dengan database MySQL,
- Saddam Surya Mardiansyah   : Mendesain dan membuat GUI menggunakan JafaFX dan Scene Builder
   
## Class Diagram

```
classDiagram

  Nasabah <|-- Individu
  Nasabah <|-- Perusahaan
  Nasabah "1"--o"*" Rekening : has
  Nasabah o-- NasabahDataModel : Data Modeling
  NasabahDataModel <-- NasabahFromController : Data Control
  NasabahDataModel --> DBHelper : DB Connection
  NasabahFromController <.. NasabahForm : Form Control
  class Nasabah{
    <<abstract>>
    #IntegerProperty idNasabah
    #StringProperty nama
    #StringProperty alama
    #ArrayList<Rekening> rekening
    +IntegerProperty nextidNasabah()
    + abstract print()
  }

  class Individu{
    -LongProperty nik
    -LongProperty npwp
    +Long getNik()
    +Long getNpwp()
    +print()
  }
  class Perusahaan{
    -StringProperty nib
    +String getNib()
    +print()
  }
  class Rekening{
    -IntegerProperty noRekening;
    -DoubleProperty saldo
    +tambahSaldo(double jumlah)
    +tartikTunai(double jumlah)
    +double getSaldo()
  }

  class NasabahDataModel{
      Connection conn
      addNasabah()
      addRekening()
      getIndividu()
      getPerusahaan()
      nextidNasabah()
      nextNoRekening()
  }

  class NasabahFromController{
      initialize()
      handleAddAccountButton()
      handleAddAccountButtonP()
      handleClearButton()
      handleClearButtonP()
      handleReloadButton()
      handleReloadButtonP()
      handleSaveButton()
      handleSaveButtonP()
      handleTambahSaldo()
      handleTambahSaldoP()
      handleTarikSaldoP()
      handleTariksaldo()
      viewDataRekening(int idNasabah)
      viewDataRekeningP(int idNasabah)
  }
  class DBHelper{
      - String DBURL
      getConnection()
      createTable();
  }
```

[![](https://mermaid.ink/img/eyJjb2RlIjoiY2xhc3NEaWFncmFtXG5cbiAgTmFzYWJhaCA8fC0tIEluZGl2aWR1XG4gIE5hc2FiYWggPHwtLSBQZXJ1c2FoYWFuXG4gIE5hc2FiYWggXCIxXCItLW9cIipcIiBSZWtlbmluZyA6IGhhc1xuICBOYXNhYmFoIG8tLSBOYXNhYmFoRGF0YU1vZGVsIDogRGF0YSBNb2RlbGluZ1xuICBOYXNhYmFoRGF0YU1vZGVsIDwtLSBOYXNhYmFoRnJvbUNvbnRyb2xsZXIgOiBEYXRhIENvbnRyb2xcbiAgTmFzYWJhaERhdGFNb2RlbCAtLT4gREJIZWxwZXIgOiBEQiBDb25uZWN0aW9uXG4gIE5hc2FiYWhGcm9tQ29udHJvbGxlciA8Li4gTmFzYWJhaEZvcm0gOiBGb3JtIENvbnRyb2xcbiAgY2xhc3MgTmFzYWJhaHtcbiAgICA8PGFic3RyYWN0Pj5cbiAgICAjSW50ZWdlclByb3BlcnR5IGlkTmFzYWJhaFxuICAgICNTdHJpbmdQcm9wZXJ0eSBuYW1hXG4gICAgI1N0cmluZ1Byb3BlcnR5IGFsYW1hXG4gICAgI0FycmF5TGlzdDxSZWtlbmluZz4gcmVrZW5pbmdcbiAgICArSW50ZWdlclByb3BlcnR5IG5leHRpZE5hc2FiYWgoKVxuICAgICsgYWJzdHJhY3QgcHJpbnQoKVxuICB9XG5cbiAgY2xhc3MgSW5kaXZpZHV7XG4gICAgLUxvbmdQcm9wZXJ0eSBuaWtcbiAgICAtTG9uZ1Byb3BlcnR5IG5wd3BcbiAgICArTG9uZyBnZXROaWsoKVxuICAgICtMb25nIGdldE5wd3AoKVxuICAgICtwcmludCgpXG4gIH1cbiAgY2xhc3MgUGVydXNhaGFhbntcbiAgICAtU3RyaW5nUHJvcGVydHkgbmliXG4gICAgK1N0cmluZyBnZXROaWIoKVxuICAgICtwcmludCgpXG4gIH1cbiAgY2xhc3MgUmVrZW5pbmd7XG4gICAgLUludGVnZXJQcm9wZXJ0eSBub1Jla2VuaW5nO1xuICAgIC1Eb3VibGVQcm9wZXJ0eSBzYWxkb1xuICAgICt0YW1iYWhTYWxkbyhkb3VibGUganVtbGFoKVxuICAgICt0YXJ0aWtUdW5haShkb3VibGUganVtbGFoKVxuICAgICtkb3VibGUgZ2V0U2FsZG8oKVxuICB9XG5cbiAgY2xhc3MgTmFzYWJhaERhdGFNb2RlbHtcbiAgICAgIENvbm5lY3Rpb24gY29ublxuICAgICAgYWRkTmFzYWJhaCgpXG4gICAgICBhZGRSZWtlbmluZygpXG4gICAgICBnZXRJbmRpdmlkdSgpXG4gICAgICBnZXRQZXJ1c2FoYWFuKClcbiAgICAgIG5leHRpZE5hc2FiYWgoKVxuICAgICAgbmV4dE5vUmVrZW5pbmcoKVxuICB9XG5cbiAgY2xhc3MgTmFzYWJhaEZyb21Db250cm9sbGVye1xuICAgICAgaW5pdGlhbGl6ZSgpXG4gICAgICBoYW5kbGVBZGRBY2NvdW50QnV0dG9uKClcbiAgICAgIGhhbmRsZUFkZEFjY291bnRCdXR0b25QKClcbiAgICAgIGhhbmRsZUNsZWFyQnV0dG9uKClcbiAgICAgIGhhbmRsZUNsZWFyQnV0dG9uUCgpXG4gICAgICBoYW5kbGVSZWxvYWRCdXR0b24oKVxuICAgICAgaGFuZGxlUmVsb2FkQnV0dG9uUCgpXG4gICAgICBoYW5kbGVTYXZlQnV0dG9uKClcbiAgICAgIGhhbmRsZVNhdmVCdXR0b25QKClcbiAgICAgIGhhbmRsZVRhbWJhaFNhbGRvKClcbiAgICAgIGhhbmRsZVRhbWJhaFNhbGRvUCgpXG4gICAgICBoYW5kbGVUYXJpa1NhbGRvUCgpXG4gICAgICBoYW5kbGVUYXJpa3NhbGRvKClcbiAgICAgIHZpZXdEYXRhUmVrZW5pbmcoaW50IGlkTmFzYWJhaClcbiAgICAgIHZpZXdEYXRhUmVrZW5pbmdQKGludCBpZE5hc2FiYWgpXG4gIH1cbiAgY2xhc3MgREJIZWxwZXJ7XG4gICAgICAtIFN0cmluZyBEQlVSTFxuICAgICAgZ2V0Q29ubmVjdGlvbigpXG4gICAgICBjcmVhdGVUYWJsZSgpO1xuICB9IiwibWVybWFpZCI6eyJ0aGVtZSI6ImRhcmsifSwidXBkYXRlRWRpdG9yIjp0cnVlLCJhdXRvU3luYyI6dHJ1ZSwidXBkYXRlRGlhZ3JhbSI6dHJ1ZX0)](https://mermaid.live/edit/#eyJjb2RlIjoiY2xhc3NEaWFncmFtXG5cbiAgTmFzYWJhaCA8fC0tIEluZGl2aWR1XG4gIE5hc2FiYWggPHwtLSBQZXJ1c2FoYWFuXG4gIE5hc2FiYWggXCIxXCItLW9cIipcIiBSZWtlbmluZyA6IGhhc1xuICBOYXNhYmFoIG8tLSBOYXNhYmFoRGF0YU1vZGVsIDogRGF0YSBNb2RlbGluZ1xuICBOYXNhYmFoRGF0YU1vZGVsIDwtLSBOYXNhYmFoRnJvbUNvbnRyb2xsZXIgOiBEYXRhIENvbnRyb2xcbiAgTmFzYWJhaERhdGFNb2RlbCAtLT4gREJIZWxwZXIgOiBEQiBDb25uZWN0aW9uXG4gIE5hc2FiYWhGcm9tQ29udHJvbGxlciA8Li4gTmFzYWJhaEZvcm0gOiBGb3JtIENvbnRyb2xcbiAgY2xhc3MgTmFzYWJhaHtcbiAgICA8PGFic3RyYWN0Pj5cbiAgICAjSW50ZWdlclByb3BlcnR5IGlkTmFzYWJhaFxuICAgICNTdHJpbmdQcm9wZXJ0eSBuYW1hXG4gICAgI1N0cmluZ1Byb3BlcnR5IGFsYW1hXG4gICAgI0FycmF5TGlzdDxSZWtlbmluZz4gcmVrZW5pbmdcbiAgICArSW50ZWdlclByb3BlcnR5IG5leHRpZE5hc2FiYWgoKVxuICAgICsgYWJzdHJhY3QgcHJpbnQoKVxuICB9XG5cbiAgY2xhc3MgSW5kaXZpZHV7XG4gICAgLUxvbmdQcm9wZXJ0eSBuaWtcbiAgICAtTG9uZ1Byb3BlcnR5IG5wd3BcbiAgICArTG9uZyBnZXROaWsoKVxuICAgICtMb25nIGdldE5wd3AoKVxuICAgICtwcmludCgpXG4gIH1cbiAgY2xhc3MgUGVydXNhaGFhbntcbiAgICAtU3RyaW5nUHJvcGVydHkgbmliXG4gICAgK1N0cmluZyBnZXROaWIoKVxuICAgICtwcmludCgpXG4gIH1cbiAgY2xhc3MgUmVrZW5pbmd7XG4gICAgLUludGVnZXJQcm9wZXJ0eSBub1Jla2VuaW5nO1xuICAgIC1Eb3VibGVQcm9wZXJ0eSBzYWxkb1xuICAgICt0YW1iYWhTYWxkbyhkb3VibGUganVtbGFoKVxuICAgICt0YXJ0aWtUdW5haShkb3VibGUganVtbGFoKVxuICAgICtkb3VibGUgZ2V0U2FsZG8oKVxuICB9XG5cbiAgY2xhc3MgTmFzYWJhaERhdGFNb2RlbHtcbiAgICAgIENvbm5lY3Rpb24gY29ublxuICAgICAgYWRkTmFzYWJhaCgpXG4gICAgICBhZGRSZWtlbmluZygpXG4gICAgICBnZXRJbmRpdmlkdSgpXG4gICAgICBnZXRQZXJ1c2FoYWFuKClcbiAgICAgIG5leHRpZE5hc2FiYWgoKVxuICAgICAgbmV4dE5vUmVrZW5pbmcoKVxuICB9XG5cbiAgY2xhc3MgTmFzYWJhaEZyb21Db250cm9sbGVye1xuICAgICAgaW5pdGlhbGl6ZSgpXG4gICAgICBoYW5kbGVBZGRBY2NvdW50QnV0dG9uKClcbiAgICAgIGhhbmRsZUFkZEFjY291bnRCdXR0b25QKClcbiAgICAgIGhhbmRsZUNsZWFyQnV0dG9uKClcbiAgICAgIGhhbmRsZUNsZWFyQnV0dG9uUCgpXG4gICAgICBoYW5kbGVSZWxvYWRCdXR0b24oKVxuICAgICAgaGFuZGxlUmVsb2FkQnV0dG9uUCgpXG4gICAgICBoYW5kbGVTYXZlQnV0dG9uKClcbiAgICAgIGhhbmRsZVNhdmVCdXR0b25QKClcbiAgICAgIGhhbmRsZVRhbWJhaFNhbGRvKClcbiAgICAgIGhhbmRsZVRhbWJhaFNhbGRvUCgpXG4gICAgICBoYW5kbGVUYXJpa1NhbGRvUCgpXG4gICAgICBoYW5kbGVUYXJpa3NhbGRvKClcbiAgICAgIHZpZXdEYXRhUmVrZW5pbmcoaW50IGlkTmFzYWJhaClcbiAgICAgIHZpZXdEYXRhUmVrZW5pbmdQKGludCBpZE5hc2FiYWgpXG4gIH1cbiAgY2xhc3MgREJIZWxwZXJ7XG4gICAgICAtIFN0cmluZyBEQlVSTFxuICAgICAgZ2V0Q29ubmVjdGlvbigpXG4gICAgICBjcmVhdGVUYWJsZSgpO1xuICB9IiwibWVybWFpZCI6IntcbiAgXCJ0aGVtZVwiOiBcImRhcmtcIlxufSIsInVwZGF0ZUVkaXRvciI6dHJ1ZSwiYXV0b1N5bmMiOnRydWUsInVwZGF0ZURpYWdyYW0iOnRydWV9)
   
## ERD Diagram

```
erDiagram
            Nasbaah ||--|{ REKENING : "has"
            Nasbaah ||..|| INDIVIDU : is
            Nasbaah ||--|| PERUSAHAAN : is
            

            REKENING{
                int noRekening
                double saldo
                int id_nasabah
            }

            Nasbaah {
                int idNasabah
                string nama
                string alamat
            }
            
            INDIVIDU{
                int id_nasabah
                long nik
                long npwp
            }
            PERUSAHAAN{
                int id_nasabah
                string nib
            }
            
```

[![](https://mermaid.ink/img/eyJjb2RlIjoiZXJEaWFncmFtXG4gICAgICAgICAgICBOYXNiYWFoIHx8LS18eyBSRUtFTklORyA6IFwiaGFzXCJcbiAgICAgICAgICAgIE5hc2JhYWggfHwuLnx8IElORElWSURVIDogaXNcbiAgICAgICAgICAgIE5hc2JhYWggfHwtLXx8IFBFUlVTQUhBQU4gOiBpc1xuICAgICAgICAgICAgXG5cbiAgICAgICAgICAgIFJFS0VOSU5He1xuICAgICAgICAgICAgICAgIGludCBub1Jla2VuaW5nXG4gICAgICAgICAgICAgICAgZG91YmxlIHNhbGRvXG4gICAgICAgICAgICAgICAgaW50IGlkX25hc2FiYWhcbiAgICAgICAgICAgIH1cblxuICAgICAgICAgICAgTmFzYmFhaCB7XG4gICAgICAgICAgICAgICAgaW50IGlkTmFzYWJhaFxuICAgICAgICAgICAgICAgIHN0cmluZyBuYW1hXG4gICAgICAgICAgICAgICAgc3RyaW5nIGFsYW1hdFxuICAgICAgICAgICAgfVxuICAgICAgICAgICAgXG4gICAgICAgICAgICBJTkRJVklEVXtcbiAgICAgICAgICAgICAgICBpbnQgaWRfbmFzYWJhaFxuICAgICAgICAgICAgICAgIGxvbmcgbmlrXG4gICAgICAgICAgICAgICAgbG9uZyBucHdwXG4gICAgICAgICAgICB9XG4gICAgICAgICAgICBQRVJVU0FIQUFOe1xuICAgICAgICAgICAgICAgIGludCBpZF9uYXNhYmFoXG4gICAgICAgICAgICAgICAgc3RyaW5nIG5pYlxuICAgICAgICAgICAgfVxuICAgICAgICAgICAgIiwibWVybWFpZCI6eyJ0aGVtZSI6ImRhcmsifSwidXBkYXRlRWRpdG9yIjpmYWxzZSwiYXV0b1N5bmMiOnRydWUsInVwZGF0ZURpYWdyYW0iOmZhbHNlfQ)](https://mermaid.live/edit/#eyJjb2RlIjoiZXJEaWFncmFtXG4gICAgICAgICAgICBOYXNiYWFoIHx8LS18eyBSRUtFTklORyA6IFwiaGFzXCJcbiAgICAgICAgICAgIE5hc2JhYWggfHwuLnx8IElORElWSURVIDogaXNcbiAgICAgICAgICAgIE5hc2JhYWggfHwtLXx8IFBFUlVTQUhBQU4gOiBpc1xuICAgICAgICAgICAgXG5cbiAgICAgICAgICAgIFJFS0VOSU5He1xuICAgICAgICAgICAgICAgIGludCBub1Jla2VuaW5nXG4gICAgICAgICAgICAgICAgZG91YmxlIHNhbGRvXG4gICAgICAgICAgICAgICAgaW50IGlkX25hc2FiYWhcbiAgICAgICAgICAgIH1cblxuICAgICAgICAgICAgTmFzYmFhaCB7XG4gICAgICAgICAgICAgICAgaW50IGlkTmFzYWJhaFxuICAgICAgICAgICAgICAgIHN0cmluZyBuYW1hXG4gICAgICAgICAgICAgICAgc3RyaW5nIGFsYW1hdFxuICAgICAgICAgICAgfVxuICAgICAgICAgICAgXG4gICAgICAgICAgICBJTkRJVklEVXtcbiAgICAgICAgICAgICAgICBpbnQgaWRfbmFzYWJhaFxuICAgICAgICAgICAgICAgIGxvbmcgbmlrXG4gICAgICAgICAgICAgICAgbG9uZyBucHdwXG4gICAgICAgICAgICB9XG4gICAgICAgICAgICBQRVJVU0FIQUFOe1xuICAgICAgICAgICAgICAgIGludCBpZF9uYXNhYmFoXG4gICAgICAgICAgICAgICAgc3RyaW5nIG5pYlxuICAgICAgICAgICAgfVxuICAgICAgICAgICAgIiwibWVybWFpZCI6IntcbiAgXCJ0aGVtZVwiOiBcImRhcmtcIlxufSIsInVwZGF0ZUVkaXRvciI6ZmFsc2UsImF1dG9TeW5jIjp0cnVlLCJ1cGRhdGVEaWFncmFtIjpmYWxzZX0)
