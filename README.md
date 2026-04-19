# Enerji İstehlakının Hibrid Modellə Proqnozlaşdırılması
Bu layihədə AEP (American Electric Power) məlumat dəsti istifadə edilərək, enerji istehlakını yüksək dəqiqliklə proqnozlaşdıran **Prophet + XGBoost** hibrid modeli qurulmuşdur.
# Modelləşdirmə Axını
# 1.Məlumatın Təmizlənməsi (Data Cleaning)
Təkrarların Silinməsi:Yay/Qış saat keçidi zamanı yaranan dublikat sətirlər təmizləndi.
Boşluqların Doldurulması:Zaman ardıcıllığında yaranan saatlıq boşluqlar 'ffill' metodu ilə bərpa edildi
# 2.Prophet Modeli (Trend və Mövsümilik)
Məlumatlar Prophet formatına ('ds' və 'y') gətirildi.
Model vasitəsilə illik, həftəlik və günlük mövsümi dalğalanmalar (seasonality) analiz edildi.
# 3.Qalıqların (Residuals) Hesablanması
Prophet modelinin real datadan kənarlaşma fərqləri (residuals) hesablandı. Bu qalıqlar XGBoost üçün hədəf dəyişəni olaraq təyin edildi.
# 4.XGBoost ilə Gücləndirmə (Hybrid Approach)
Feature Engineering: Zaman göstəricilərindən yeni rəqəmsal xüsusiyyətlər (saat, gün, ay, rüb) yaradıldı.
Səhv Düzəltmə: XGBoost modeli Prophet-in qaçırdığı qeyri-xətti asılılıqları öyrənmək üçün qalıqlar üzərində öyrədildi.
# 5.Final Birləşdirmə və Qiymətləndirmə
Hibrid Proqnoz:'Final = Prophet_Forecast + XGBoost_Correction'
Nəticə:Model **4.90% MAPE** (Mean Absolute Percentage Error) ilə yüksək dəqiqlik nümayiş etdirdi.
