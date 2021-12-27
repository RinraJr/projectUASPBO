# Final Project PBO
Kelompok 6\
Anggota : 
1. Saddam Surya Mardiansyah   - 2017051014
2. Bagus Tito Dwi Saputra     - 2057051018
3. Mahesa Yudhistira          - 1917051029
4. Raesha Salsabila           - 1957051006

Pembagian Tugas :
1. 
     


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
