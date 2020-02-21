# SoalShiftSISOP20_modul1_Y35

## Jawaban Soal Shift Sistem Operasi 2020

## Modul 1

Oleh: 

* 05311840000020 Milenia Ulwan Zafira
* 05311840000042 I Komang Aditya Mahadiharja

## Daftar Isi
* [1. Filter Data dengan AWK](#1-filter-data-dengan-awk)
* [3. PDKT Kusuma](#3-pdkt-kusuma)
- - - 

## 1. Filter Data dengan AWK
#### soal1.sh
```
#!/bin/bash

#(a)
echo "a) Region profit terkecil: "
awk -F'\t' 'FNR > 1{SUM[$13] +=$21} END{for (j in SUM) print j, SUM[j]}' Sample-Superstore.tsv | sort -gk2 | awk 'FNR < 2{print$1}'

#(b)
echo "b) 2 State profit terkecil: "
awk -F'\t' 'FNR > 1{SUM[$11] +=$21} END{for (j in SUM) print j, SUM[j]}' Sample-Superstore.tsv | sort -gk2  | awk 'FNR < 3{printf"%s \n", $1$2$3$4$5$6}'

#(c)
echo "c) 10 nama Produk profit terkecil: "
awk -F'\t' '{if($11 =="District of Columbia" && $11 =="New Hampshire") FNR > 1{SUM[$17] +=$18} END{for (j in SUM) print j, SUM[j]}' Sample-Superstore.tsv | sort -gk2  | awk 'FNR < 11{printf $1$2$3$4$5$6$7$8$9}'
```
####Penjelasan
#####Soal \n
Whits adalah seorang mahasiswa teknik informatika. Dia mendapatkan tugas praktikum
untuk membuat laporan berdasarkan data yang ada pada file “Sample-Superstore.tsv”.
a.Tentukan wilayah bagian (region) mana yang memiliki keuntungan (profit) paling
sedikit
b. Tampilkan 2 negara bagian (state) yang memiliki keuntungan (profit) paling
sedikit berdasarkan hasil poin a
c. Tampilkan 10 produk (product name) yang memiliki keuntungan (profit) paling
sedikit berdasarkan 2 negara bagian (state) hasil poin b

#####Solusi:
a. menentukan region pada $13 yang memiliki profit $21 paling kecil dengan ``awk -F'\t' 'FNR > 1{SUM[$13] +=$21} END{for (j in SUM) print j, SUM[j]}' `` lalu sorting dan print ``| sort -gk2 | awk 'FNR < 2{print$1}'``
b. menentukan state pada $11 yang memiliki profit paling kecil dangan ``awk -F'\t' 'FNR > 1{SUM[$11] +=$21} END{for (j in SUM) print j, SUM[j]}'`` lalu sorting dan print 2 state dengan nilainya ``| sort -gk2  | awk 'FNR < 3{printf"%s \n", $1$2$3$4$5$6}'``
c. setelah ditemukan di 1b bahwa state profit terkecil adalah District of Columbia dan New Hampshire maka dibuat code ``awk -F'\t' '{if($11 =="District of Columbia" && $11 =="New Hampshire") FNR > 1{SUM[$17] +=$18} END{for (j in SUM) print j, SUM[j]}'`` dan di sort serta print ``| sort -gk2  | awk 'FNR < 11{printf $1$2$3$4$5$6$7$8$9}'`` ->> salah/belum benar

## 3.PDKT Kusuma
#### soal3.sh
```
#!/bin/bash

tes=`ls | grep "pdkt_kusuma_" | cut -d "_" -f 3 | sort -n | tail -1`
echo $tes

if [[ $tes < 1 ]]
then
tes=0
fi

a=`expr $tes + 1`
b=`expr $tes + 28`

for ((i=a;i<b;i=i+1))
do
wget -a wget.log -O "pdkt_kusuma_$i" https://loremflickr.com/320/240/cat
done
```
#### crontab
```
5 6-23/8 * * 0-5  /home/milenfifi/Downloads/soal3.sh
```
