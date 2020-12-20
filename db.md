- [Ujian Online Database](#ujian-online-database)
  - [ACCOUNT](#account)
      - [Users](#users)
      - [UserAsesi](#userasesi)
      - [UserAsesiCustomData](#userasesicustomdata)
      - [AsesiCustomData *ini untuk custom data apl01](#asesicustomdata-ini-untuk-custom-data-apl01)
      - [AsesiUnitKompetensiDokumen *ini untuk apl02](#asesiunitkompetensidokumen-ini-untuk-apl02)
      - [AsesiSertifikasiUnitKompetensiElement](#asesisertifikasiunitkompetensielement)
      - [UserAsesor](#userasesor)
      - [UserTuk](#usertuk)
      - [Tuk](#tuk)
      - [TukBanks](#tukbanks)
  - [LMS](#lms)
      - [Sertifikasi](#sertifikasi)
      - [SertifikasiTuk](#sertifikasituk)
      - [SertifikasiUnitKompentensi](#sertifikasiunitkompentensi)
      - [SertifikasiUnitKompetensiElement](#sertifikasiunitkompetensielement)
      - [Soal](#soal)
      - [SoalUnitKompetensi](#soalunitkompetensi)
      - [SoalPilihanGanda](#soalpilihanganda)
      - [SoalPaket](#soalpaket)
      - [SoalPaketitem](#soalpaketitem)
  - [ASESOR](#asesor)
      - [UjianJadwal](#ujianjadwal)
      - [UjianAsesiAsesor](#ujianasesiasesor)
      - [UjianAsesiJawaban (untuk menyimpan soal yg generate untuk user)](#ujianasesijawaban-untuk-menyimpan-soal-yg-generate-untuk-user)
      - [UjianAsesiJawabanPilihan  (untuk menyimpan jawabannya)](#ujianasesijawabanpilihan--untuk-menyimpan-jawabannya)
  - [ORDER](#order)
      - [Order](#order-1)

# Ujian Online Database

## ACCOUNT

#### Users
- id (bigInt) (autoIncerment)
- password (string)
- email (string)
- type (string) (admin/tuk/assesor/asessi)
- status (tinyInt) (active/inactive/suspend)
- media_url (string) (url)
- created_at (datetime)
- updated_at (datetime)
- is_active

#### UserAsesi
- id (bigInt) (autoIncerment)
- user_id (bigInt)
- name (string)
- address (text)
- gender (boolean) (true = pria)
- birth_place (string)
- birth_date (date)
- no_ktp (string)
- pendidikan_terakhir (dropdown) (sma/smk/d1/d2/d3/s1/s2)
- has_job (boolean) (bekerja = true/tidak = false)
- job_title (string)
- job_address (text)
- media_url_sign_admin (string) (canvas) *untuk ttd admin yg approve
- user_id_admin
- media_url_sign_user *untuk ttd user
- note_admin (text)
- is_verified (boolean)
- verification_note

#### UserAsesiCustomData
- user_id_asesi
- title
- input_type
- value
- is_verified
- verification_note

#### AsesiCustomData *ini untuk custom data apl01
- id (bigInt) (autoIncerment)
- title (string)
- input_type (string) (text, dropdown, upload_image, upload_pdf)

#### AsesiUnitKompetensiDokumen *ini untuk apl02
- id
- user_id_asesi
- unit_kompetensi_id
- order (urutan diisi manual)
- sertifikasi_id (string)
- kode_unit_kompetensi (string) (manual input)
- title (string)
- sub_title (string)

#### AsesiSertifikasiUnitKompetensiElement
- id (bigInt) (autoIncerment) 
- user_id_asesi
- unit_kompetensi_id (bigInt)
- desc (text)
- upload_instruction (string)
- media_url
- is_verified
- verification_note

#### UserAsesor
- id (bigInt) (autoIncerment)
- user_id (bigInt)
- met (string) (kode assesor)
- name (string)
- expired_date (date)
- address (text)

#### UserTuk
- id
- user_id_tuk
- tuk_id

#### Tuk
- id (bigInt) (autoIncerment)
- code (string)
- title (string)
- telp (string)
- address (text)
- type (string) (tukmandiri/sewaktu/jarakjauh)

#### TukBanks
- id (bigInt) (autoIncerment)
- tuk_id (bigInt)
- bank_name (string) - (Mandiri, BNI, BRI, BCA, BTN, Permata)
- account_number (string)
- account_name (string)

## LMS

#### Sertifikasi
- id (bigInt) (autoIncerment)
- nomor_skema (string) (input manual)
- title (string)
- original_price_baru (float)
- original_price_perpanjang (float)
- jenis_sertifikasi (string) (baru/perpanjang)
- is_active (boolean)

#### SertifikasiTuk
- sertifikasi_id
- tuk_id
- tuk_price_baru
- tuk_price_perpanjang

#### SertifikasiUnitKompentensi
- id (bigInt) (autoIncerment) 
- order (urutan diisi manual)
- sertifikasi_id (string)
- kode_unit_kompetensi (string) (manual input)
- title (string)
- sub_title (string)

#### SertifikasiUnitKompetensiElement
- id (bigInt) (autoIncerment) 
- unit_kompetensi_id (bigInt)
- desc (text)
- upload_instruction (string)

#### Soal
- id (bigInt) (autoIncerment)
- question (text)
- question_type (essay, multiple_option)
- answer_essay
- answer_option (A, B, C, D)
- max_score

#### SoalUnitKompetensi
- soal_id
- unit_kompetensi_id

#### SoalPilihanGanda
- id
- soal_id
- option
- label (A, B, C, D)

#### SoalPaket
- id
- title
- sertifikasi_id

#### SoalPaketitem
- id
- soal_paket_id
- soal_id

## ASESOR

#### UjianJadwal
- id
- tanggal
- title
- paket_A (10 soal)

#### UjianAsesiAsesor
- id_asesi_asesor
- asesi_id
- ujian_jadwal_id
- sertifikasi_id
- asesor_id
- order_id
- status (menunggu, penilaian, selesai)
- is_kompeten (t/f)
- final_score_percentage

#### UjianAsesiJawaban (untuk menyimpan soal yg generate untuk user)
- id_asesi_asesor
- soal_id
- question (text)
- question_type (essay, multiple_option)
- answer_essay
- answer_option (A, B, C, D)
- urutan (1, 2 dst)
- user_answer
- catatan_asesor
- max_score 
- final_score

#### UjianAsesiJawabanPilihan  (untuk menyimpan jawabannya)
- id_asesi_asesor_Jawaban
- option
- label (A, B, C, D)

## ORDER

#### Order
- user_id_asesi
- sertifikasi_id
- tuk_id
- tipe_sertifikasi (baru, perpanjang)
- kode_sertifikat
- original_price
- tuk_price
- status (waiting_payment, pending_verification, payment_rejected, payment_verified, canceled, completed) complete kalau udah di assign asesor
- comment_rejected
- comment_verification
- transfer_from_bank_name 
- transfer_from_bank_account
- transfer_from_bank_number
- transfer_to_bank_name
- transfer_to_bank_account
- transfer_to_bank_number
- transfer_date
- media_url_bukti_transfer
- expired_date
- created_at
- updated_at


#3. projects/lms#
