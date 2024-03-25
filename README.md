create database school_library;
use school_library;
create table uyeler(

uyeNo int not null primary key identity(1,1),
uyeAdi nvarchar(50)not null,
uyeSoyadi nvarchar(50) not null,
eposta nvarchar(100) not null,
cinsiyet char(2) not null,
telefon int
);

create table adresler(

adresNo int not null primary key identity(1,1),
Sehir nvarchar(50)not null,
Mahalle nvarchar(50) not null,
BinaNo int not null,
cadde nvarchar(200) not null,
ulke nvarchar(50),
postaKodu int
);
ALTER TABLE uyeler ADD adresNo int constraint FK_uyeler_adres Foreign key (adresNo) references ADRESLER (adresNo);

create table kutuphane(
kutuphane int not null identity (1,1) PRIMARY KEY,
kutuphaneIsmı nvarchar(50),
aciklama nvarchar(500),
adresNo int constraint FK_adresler_kutuphane FOREIGN KEY (adresNo) references adresler(adresNo)
);

create table bulunur1(
miktar int not null primary key identity(1,1),
kutuphaneNo int constraint FK_kutuphane_bulunur1 foreign key(kutuphaneNo) references kutuphane(kutuphaneNo),
ISBN nvarchar(50) constraint FK_kitaplar_bulunur1 foreign key(ISBN) references kitaplar(ISBN),
);

create table yazar(
yazarNo int not null primary key identity(1,1),
yazarNumber int constraint FK_yazarlar_yazar foreign key(yazarNumber) references yazarlar(yazarNumber),
ISBN nvarchar(50) constraint FK_kitap_yazar foreign key(ISBN) references kitaplar(ISBN),
);

create table bulunur2(
bulunurNo int not null primary key identity(1,1),
kategoriNo int constraint FK_kategoriler_bulunur2 foreign key(kategoriNo) references kategoriler(kategoriNo),
ISBN nvarchar(50) constraint FK_kitaplar_bulunur2 foreign key(ISBN) references kitaplar(ISBN),
);
