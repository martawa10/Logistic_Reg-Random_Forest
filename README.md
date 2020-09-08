## HR Analytics case study

Duża firma o nazwie XYZ zatrudnia w danym momencie około 4000 pracowników. Jednak każdego roku około 15% pracowników odchodzi z firmy. Zarząd uważa, że odejście pracowników na własną rękę lub z powodu ich zwolnienia jest niekorzystne dla firmy z następujących powodów:
Projekty byłych pracowników ulegają opóźnieniu, co utrudnia dotrzymanie terminów i powoduje utratę reputacji wśród konsumentów i partnerów
Dział HR musi być większy w celu rekrutacji nowych talentów
Najczęściej nowi pracownicy muszą być przeszkoleni do pracy i / lub mieć czas na aklimatyzację w firmie
Celem przedstawionej pracy jest zaproponowanie modelu przewidującego prawdopodobieństwo odejścia pracownika z pracy. Dane użyte do zadania znajdują się na stronie: https://www.kaggle.com/vjchoudhary7/hr-analytics-case-study#general_data.csv

## Modele użyte w projekcie:
- regresja logistyczna
- las losowy

## Wnioski.  Podsumowanie - porównanie modeli

Rozpatrując confusion_matrix dla zadanego problemu badawczego oraz porównując wyniki dla różnych progów odcięcia ważne jest poleprzenie klasyfikacji TN (Osób, które odeszły z pracy i zostały poprawnie sklasyfikowane) oraz minimalizacja klasyfikacji FP (Osoby które odeszły z pracy, sklasyfikowane jako osoby nadal pracujące).

W modelu regresji logistycznej wartości dla progu odcięcia Youdena w porównaniu z progiem odcięcia 0,5 zmieniła się następująco:

TN wzrosło z 10 do 130 (prawdziwie negatywnych klasyfikacji)
FP zmniejszyło się z 222 do 102 (fałszywie pozytywnych klasyfikacji)
tzn. dla progu odcięcia optymalnego wartości te znacznie się poprawiły. Zmniejszenie progu odcięcia z 0,5 na próg optymalny Youdena powoduje znaczne zwiększenie sensitivity (czułości modelu), a co za tym idzie zmniejszenie specificity. Sensitivity wzrosło z 0,04 do 0,56.

FPR = 1- specifity w związku z czym zwiększenie wartości TPR (True Positive Rate) jest związane również ze zwiększeniem wartości FPR (False Positive Rate).

W modelu lasu losowego wartości dla progu odcięcia Youdena w porównaniu z progiem odcięcia 0,5 zmieniła się następująco:

TN wzrosło z 188 do 199 (prawdziwie negatywnych klasyfikacji)
FP zmniejszyło się z 39 do 238 (fałszywie pozytywnych klasyfikacji)
W modelu lasu losowego wyniki również uległy poprawie jednak zmiana nie jest tak duża, wynika to z tego że sam model przy progu odcięcia 0,5 ma już bardzo wysoką skuteczność i zmiana progu nieznacznie wpływa na jego polepszenie. Sensitivity oraz Specificity praktycznie się nie zmieniło.

W obu przypadkach próg odcięcia Youdena polepszył wyniki modelu, jednak w przypadku regresji logistycznej różnica jest znacznie większa. W przypadku modelu lasu losowego wyniki klasyfikacji przy obu progach są zbliżone. W obu przypadkach optymalny próg odcięcia jest<0.5.

Efektywniejszym modelem dla analizowanego zagadnienia w przypadku obu progów odcięcia będzie więc model lasu lasowego. Jego jakość predykcji jest wysoka.
