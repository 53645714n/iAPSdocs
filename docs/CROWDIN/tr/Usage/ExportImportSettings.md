# Dışa aktarma/içe aktarma ayarları

## Ayarları ne zaman dışa aktarmalıyım?

Öngörülemeyenlere hazırlıklı olun. Önemli ayarları yanlışlıkla değiştirebilir ve değişiklikleri geri almakta sorun yaşayabilirsiniz. Telefonunuz kırılabilir veya çalınabilir. Bulunduğunuz duruma kolayca geri dönmek için ayarlar düzenli olarak dışa aktarılmalıdır.

En iyi zamanlama, ayarların değiştirilmesinden veya bir hedefin tamamlanmasından sonra dışa aktarmaktır.

Dışa aktarılan ayarlar, telefondan bir buluta veya bilgisayarınıza kopyalanmalıdır, en iyisi iki farklı konuma da kopyalamaktır. Böylece AAPS telefonunuzun kaybolmasına veya zarar görmesine hazırsınız ve sıfırdan başlamak zorunda değilsiniz.

Bir Windows 10 bilgisayarında şöyle görünür:

```{image} ../images/AAPS_ExImportSettingsWin.png
:alt: "Bilgisayara ba\u011Fl\u0131 AndroidAPS telefonda Preferences klas\xF6r\xFC"
```

## Dışa aktarılan bilgiler

Diğerlerinin yanı sıra aşağıdaki bilgiler, dışa aktarılan ayarların bir parçasıdır:

- [Otomasyon](../Usage/Automation.md) olayları
- [Konfigürasyon ayarları](../Configuration/Config-Builder.md)
- [Yerel profil](../Configuration/Config-Builder#local-profile) ayarları
- [Görevler](../Usage/Objectives.md) durum dahil. [durumları dahil](../Usage/Objectives#objective-3-prove-your-knowledge)
- [Tercihler](../Configuration/Preferences.md) NS Client ayarları [dahil](../Configuration/Preferences#nsclient)

## Şifreli yedekleme formatı

Ayarların yedeği, [Tercihler](../Configuration/Preferences#master-password) içinde ayarlanabilen bir ana parola ile şifrelenir.

## Dışa aktarma ayarları

- Hamburger menü (ekranın sol üst kısmında)
- Bakım
- Dışa aktarma ayarları

```{image} ../images/AAPS_ExportSettings1.png
:alt: "AndroidAPS d\u0131\u015Fa aktarma ayarlar\u0131 1"
```

- Dışa aktarma tarihi ve saati dosya adına otomatik olarak eklenecek ve yol ile birlikte görüntülenecektir.
- 'Tamam'ı tıklayın.
- [ana parolayı](../Configuration/Preferences#master-password) girin ve 'Tamam'ı tıklayın.
- Ekranın alt kısmında başarılı dışa aktarma görünecektir.

```{image} ../images/AAPS_ExportSettings2.png
:alt: "AndroidAPS d\u0131\u015Fa aktarma ayarlar\u0131 2"
```

## İçe aktarma ayarları

**Aktif bir Pod varken ayarları içe aktarmayın** - ayrıntılar için [Omnipod sayfasına bakın](../Configuration/OmnipodEros#import-settings-from-previous-aaps).

- Hamburger menü (ekranın sol üst kısmında)
- Bakım
- İçe aktarma ayarları

```{image} ../images/AAPS_ImportSettings1.png
:alt: "AndroidAPS i\xE7e aktarma ayarlar\u0131 1"
```

- Telefonunuzdaki AAPS/preferences/ klasöründeki tüm dosyalar listede gösterilecektir.
- Dosyayı seçin.
- 'Tamam'ı tıklayarak içe aktarmayı onaylayın.
- [ana parolayı](../Configuration/Preferences#master-password) girin ve 'Tamam'ı tıklayın.

```{image} ../images/AAPS_ImportSettings2.png
:alt: "AndroidAPS i\xE7e aktarma ayarlar\u0131 2"
```

- Aktarılacak dosyaya ilişkin ayrıntılar gösterilecektir.
- İçe aktarmayı iptal etmek için son şansınız.
- 'İçe Aktar'ı tıklayın.
- 'Tamam'ı tıklayarak mesajı onaylayın.
- İçe aktarılan tercihleri etkinleştirmek için AAPS yeniden başlatılacak.

### Dana RS kullanıcıları için not

- Pompa bağlantı ayarları da içe aktarıldığından, yeni telefonunuzdaki AAPS pompayı zaten "bilir" ve bu nedenle bir bluetooth taraması başlatmaz. Fakat telefonunuz henüz pompa ile eşleşmemiştir.
- Lütfen yeni telefonu ve pompayı manuel olarak eşleştirin.

### Ayarları önceki sürümlerden içe aktarın (AAPS 2.7'den önce)

- "Eski" ayarlar dosyası ('AndroidAPSPreferences' olarak adlandırılır - dosya uzantısı olmadan) akıllı telefonunuzun kök klasöründe olmalıdır (/storage/emulated/0).
- "Eski" dosyayı yeni dışa aktarılan ayarlarla (AAPS/tercihler) aynı klasöre koymayın.
- İçe aktarma iletişim kutusundaki listenin en altında "eski" dosyayı bulacaksınız.

## Ayarlar dosyasını transfer etme

- Ayarlar dosyasını yeni bir telefona aktarmanın en iyi yolu USB kablosu veya bulut hizmetidir (yani Google Drive).
- Kılavuzlar web'de bulunabilir, [Android yardım sayfaları](https://support.google.com/android/answer/9064445?hl=en).
- Transfer etmeyle ilgili sorun yaşıyorsanız, dosya transferinin başka bir yolunu deneyin.