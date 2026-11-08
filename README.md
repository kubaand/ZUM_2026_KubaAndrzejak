# Projekt końcowy ZUM 2026/2027

To repozytorium rozwijasz przez cały semestr. Górna część tego pliku mówi, jak pracować. Dolna część to dokumentacja Twojego projektu, którą uzupełniasz w kolejnych zadaniach.

## Jak pracować z tym repozytorium

### Co robisz

Przeprowadzasz jeden wiarygodny eksperyment nadzorowanej klasyfikacji jednolabelowej. Każdy przykład ma dokładnie jedną klasę docelową. Pracujesz na tekście, obrazie, audio albo danych multimodalnych. Projekt jest indywidualny.

Projekt ma trzy poziomy:
1. **Poziom A. Punkt odniesienia.** Prosty, sensowny baseline.
2. **Poziom B. Podejście pretrained.** Co najmniej jedno podejście pretrained. Dobrym pierwszym krokiem jest zamrożony encoder i prosty klasyfikator. Fine tuning nie jest obowiązkowy.
3. **Poziom C. Jedno uzasadnione rozszerzenie.** Odpowiada na to samo pytanie projektu i nie zmienia zmiennej docelowej ani problemu klasyfikacyjnego.

Pełne zasady są w pliku [PROJECT_RULES.md](PROJECT_RULES.md). Przeczytaj je przed zgłoszeniem tematu.

### Od czego zacząć

1. Utwórz własne repozytorium z tego szablonu: wybierz „Use this template”, a następnie „Create a new repository”.
2. Nazwij repozytorium `ZUM_2026_ImięNazwisko`.
3. Repozytorium może być publiczne albo prywatne. Jeśli jest prywatne, dodaj konto prowadzącej wskazane na platformie kursu. Jeśli Twoje dane zawierają informacje osobowe albo wrażliwe, przeczytaj najpierw zasadę o prywatności w [zasadach projektu](PROJECT_RULES.md).
4. Przeczytaj [instrukcję zgłoszenia tematu](assignments/00_topic_submission.md) i zgłoś temat.

### Kolejność i terminy

Wszystkie terminy przypadają w niedzielę o godzinie 23:59. Wszystko oddajesz na platformie kursu.

| Etap | Instrukcja | Termin | Punkty | Co oddajesz |
|---|---|---|---|---|
| Zgłoszenie tematu | [00_topic_submission.md](assignments/00_topic_submission.md) | 21 października 2026 | 0, obowiązkowe | wypełniony szablon zgłoszenia |
| Zadanie 1 | [01_data_and_protocol.md](assignments/01_data_and_protocol.md) | 8 listopada 2026 | 15 | link do repozytorium i tag `task-1` |
| Akceptacja artykułu spoza listy | [scientific_paper_review.md](assignments/scientific_paper_review.md) | 22 listopada 2026 | 0, obowiązkowe dla źródeł spoza listy | pełny opis bibliograficzny oraz DOI albo oficjalny link |
| Zadanie 2 | [02_baseline.md](assignments/02_baseline.md) | 29 listopada 2026 | 15 | link i tag `task-2` |
| Artykuł naukowy | [scientific_paper_review.md](assignments/scientific_paper_review.md) | 6 grudnia 2026 | 10, poza projektem | plik PDF albo Markdown |
| Zadanie 3 | [03_pretrained.md](assignments/03_pretrained.md) | 20 grudnia 2026 | 20 | link i tag `task-3` |
| Zadanie 4 | [04_extension.md](assignments/04_extension.md) | 17 stycznia 2027 | 20 | link i tag `task-4` |
| Zadanie 5 | [05_final_evaluation.md](assignments/05_final_evaluation.md) | 31 stycznia 2027 | 30 | link oraz tagi `final-freeze` i `task-5` |

Projekt jest wart 100 punktów. Artykuł jest osobnym zadaniem za 10 punktów.

### Final test w skrócie

1. Final test wydzielasz w Zadaniu 1 i od razu go zamrażasz.
2. Do końca Zadania 4 nie uruchamiasz na nim żadnego modelu. Wszystkie porównania i wybór systemu robisz na validation.
3. W Zadaniu 5 wybierasz dokładnie jeden finalny system, zapisujesz go w `final_system.md` i tworzysz tag `final-freeze`.
4. Nie trenujesz systemu ponownie na `train + validation` ani na żadnym większym zbiorze.
5. Dopiero potem uruchamiasz final test, jeden raz, tylko dla tego systemu. Wynik testu nie może zmienić systemu.

Szczegóły są w [zasadach projektu](PROJECT_RULES.md), w części „Zasady final test”.

### Tagi Git

Każde oddanie wskazuje commit oznaczony tagiem. Oceniamy stan repozytorium z tego commita.

```bash
git add .
git commit -m "Zadanie 1: protokół i podział danych"
git tag -a task-1 -m "Zadanie 1"
git push origin main
git push origin task-1
```

Polecenie `git ls-remote --tags origin` pokazuje, czy tag jest już na GitHub. Tag możesz też utworzyć na stronie GitHub w zakładce Releases. Nie przesuwaj i nie usuwaj tagów po oddaniu.

### Gdzie co zapisujesz

| Miejsce | Co tam trafia |
|---|---|
| `README.md`, część dolna | dokumentacja projektu |
| `notebooks/` | notebooki kolejnych etapów |
| `src/` | kod wspólny dla notebooków (opcjonalnie) |
| `splits/` | identyfikatory przykładów train, validation i final test ([opis formatu](splits/README.md)) |
| `results/` | metryki i predykcje na validation, dziennik eksperymentów, wynik final test (dopiero po `final-freeze`); [opis układu](results/README.md) |
| `final_system.md` | zapis finalnego systemu (Zadanie 5); [szablon](templates/final_system_template.md) |
| `data/sample/` | mała próbka danych, jeśli licencja i zasady prywatności na to pozwalają |
| `templates/` | szablony do skopiowania |

### Czego nie wrzucasz

* pełnych zbiorów danych;
* dużych wag modeli i checkpointów (przechowujesz je poza repozytorium i opisujesz, gdzie są);
* danych, próbek ani identyfikatorów umożliwiających identyfikację osób;
* haseł, tokenów i kluczy API;
* plików tymczasowych środowiska.

Plik `.gitignore` blokuje typowe przypadki, ale to Ty odpowiadasz za zawartość repozytorium.

### Jak oceniamy

Liczy się poprawność metodologiczna, uzasadnienie decyzji i jakość analizy. Wysokość wyniku nie jest sama w sobie kryterium. Projekt z niższym F1, wykonany poprawnie i dobrze przeanalizowany, może dostać więcej punktów niż projekt z bardzo wysokim wynikiem uzyskanym przy wycieku danych. Kryteria każdego zadania są w jego instrukcji, a rubryka ogólna w [zasadach projektu](PROJECT_RULES.md).

---

# Dokumentacja projektu

Uzupełniaj sekcje w zadaniach podanych w nawiasach. Zastępuj teksty w nawiasach kwadratowych.

## Informacje ogólne

* Tytuł: [Porównanie skuteczności klasycznych metod uczenia maszynowego i modeli pretrained w klasyfikacji COVID-19 na podstawie zdjęć RTG klatki piersiowej.]
* Autor: [Kuba Andrzejak]
* Modalność: [obraz]
* Problem klasyfikacji: [Nadzorowany, binarna klasyfikacja jednolabelowa. Każdemu zdjęciu przypisana jest jedna etykieta, negative albo positive.]

## Problem i pytanie eksperymentalne (Zadanie 1)

[Czy zastosowanie modelu pretrained ResNet50 z wykorzystaniem transfer learning pozwala uzyskać wyższą skuteczność klasyfikacji zdjęć RTG niż klasyczny klasyfikator Logistic Regression wykorzystujący wartości pikseli?]

## Dane i licencja (Zadanie 1)

[# Źródło i link - Kaggle - https://www.kaggle.com/datasets/andyczhao/covidx-cxr2

License: [GNU AFFERO GENERAL PUBLIC LICENSE Version 3, 19 November 2007](https://github.com/lindawangg/COVID-Net/blob/master/LICENSE.md)

* covid-chestxray-dataset

Multiple Licenses: Apache 2.0, Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0), Attribution 4.0 International (CC BY 4.0)

* Figure 1 COVID-19 Chest X-ray Dataset Initiative

License: [GNU General Public License (GPLv3)](https://www.gnu.org/licenses/gpl-3.0.en.html)

* Actualmed COVID-19 Chest X-ray Dataset Initiative

License: [GNU General Public License (GPLv3)](https://www.gnu.org/licenses/gpl-3.0.en.html)

* COVID-19 Radiography Database - Version 3

Multiple Licenses: Attribution 3.0 Unported (CC BY 3.0), Attribution 4.0 International (CC BY 4.0), Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)

* RSNA Pneumonia Detection Challenge

License: [Terms of Use and Attribution](https://www.rsna.org/-/media/Files/RSNA/Education/AI-resources-and-training/AI-image-challenge/pneumonia-detection-challenge-terms-of-use-and-attribution.ashx)

* RSNA International COVID-19 Open Radiology Database (RICORD)

License: [Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/)

* BIMCV-COVID19+: a large annotated dataset of RX and CT images of COVID19 patients

License:Data Research Use Agreement (https://github.com/BIMCV-CSUSP/BIMCV-COVID-19/blob/master/BIMCV-COVID19%2B/LICENSE.md)

* Stony Brook University COVID-19 Positive Cases (COVID-19-NY-SBU)

License:[TCIA Data Usage Policy](https://www.cancerimagingarchive.net/data-usage-policies-and-restrictions/), [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/)

# Sposób pobrania 

Dane pobrano i rozpakowano lokalnie

# Liczba przykładów

Oryginalne manifesty zawierają 84 818 wpisów i 45 342 unikalne ID pacjentów

# Lista klas 

[negative, positive]

# Sposób oznaczenia etykiet 

Etykiety przejęto z manifestów dostawcy. Nie wykonywano samodzielnej oceny medycznej obrazów.

# Znane ograniczenia

* Powiązanie źródła z klasą. Niektóre kolekcje zawierają wyłącznie jedną klasę. rsna dostarcza zdjęcia negatywne, a m.in. sirm, ricord i stonybrook pozytywne. Model może wykorzystywać napisy, kontrast lub inne cechy kolekcji do przewidywania etykiety.

* Różne rozkłady danych. W train około 84,27% zdjęć jest pozytywnych, podczas gdy validation i final test są niemal zbalansowane. Między podzbiorami różni się również udział źródeł, co może wpływać na wyniki.

* Niepełna identyfikacja pacjentów. Wykryto kopie obrazów przypisane różnym ID. Utworzono grupy powiązanych identyfikatorów, jednak ich rozłączność nie gwarantuje pełnej rozłączności rzeczywistych osób.

* Częściowa kontrola podobnych kopii. Dokładne duplikaty sprawdzono w całym zbiorze. Dodatkowo oceniono ręcznie 66 par wybranych z kandydatów dHash i rankingu SSIM. Kopie o innych skrótach, po przycięciu, obrocie lub zmianach obrazu mogły pozostać niewykryte.

* Zależność zdjęć jednego pacjenta. Jedna osoba może mieć wiele obrazów. Metryki liczone na poziomie zdjęć nadają większy wpływ pacjentom z większą liczbą badań.

* Jakość etykiet i obrazów. Etykiety przejęto z manifestów bez niezależnej weryfikacji medycznej. Audyt wykrył jeden identyczny obraz ze sprzecznymi etykietami. Obrazy różnią się także rozmiarem, jasnością, kadrowaniem i oznaczeniami.

* Ograniczona generalizacja. Podział ocenia nowych pacjentów w mieszaninie źródeł reprezentowanej w COVIDx. Wynik nie określa skuteczności na nowych szpitalach, aparaturze ani populacjach.

* Brak walidacji klinicznej. Wyniki klasyfikacji na COVIDx nie stanowią potwierdzenia przydatności modelu do diagnozowania pacjentów.]



## Protokół (Zadanie 1)

* Jednostka generalizacji: [pacjent]
* Podział: [train/validation/test, skorygowany po audycie. Usunięto nadmiarowe dokładne kopie oraz oba wpisy obrazu ze sprzecznymi etykietami. Dla grup powiązanych ID występujących w kilku podzbiorach zachowano pierwszeństwo test → validation → train, wykluczając wszystkie zdjęcia powiązanych ID z podzbiorów o niższym pierwszeństwie. Łącznie wykluczono 118 wpisów. Sprawdzono rozłączność utworzonych grup oraz unikalność dokładnych haszy w końcowym zbiorze.]
* Metryka główna i pomocnicze: [główną metryką jest macro-F1, przypisująca równą wagę wynikowi F1 każdej klasy. Jest to uzasadnione niezbalansowaniem train, w którym około 84,27% zdjęć ma etykietę pozytywną. Pomocniczo raportowane będą accuracy, precision i recall klasy pozytywnej oraz macierz pomyłek. Metryki będą liczone na poziomie zdjęć.]
* Seed: [42]
* Final test: zamrożony w commicie z tagiem `task-1`, identyfikatory w `splits/`. Jeśli podział był później poprawiany, podaj commit poprawionej wersji i opisz zmianę w dzienniku zmian.

| Zbiór | Liczba przykładów | Liczba niezależnych jednostek |
|---|---|---|
| train | 67782 | 35400 |
| validation | 8451 | 5161 |
| final test | 8466 | 4721 |

## Wyniki (Zadania 2 do 5)

Wyniki na validation:

| Podejście | Zadanie | Metryka główna | Metryki pomocnicze | Czas i sprzęt | Uwagi |
|---|---|---|---|---|---|
| Trivial baseline | 2 | | | | |
| Baseline | 2 | | | | |
| Podejście pretrained | 3 | | | | |
| Rozszerzenie | 4 | | | | |

Wynik na final test, wyłącznie dla finalnego systemu i dopiero po utworzeniu tagu `final-freeze`:

| System | Metryka główna | Metryki pomocnicze |
|---|---|---|
| [nazwa z `final_system.md`] | | |

## Finalny system (Zadanie 5)

Pełny zapis jest w `final_system.md`. [Krótkie uzasadnienie wyboru na podstawie validation.]

## Reprodukcja

[Wersja Pythona, instalacja środowiska, pobranie danych, kolejność uruchamiania notebooków albo skryptów, sprzęt, przybliżony czas.]

## Ograniczenia

[Ograniczenia danych, protokołu i wyników. Czego wynik nie dowodzi.]

## Dziennik zmian

| Data | Zadanie | Co zmieniono i dlaczego |
|---|---|---|
| 08.11.2026 | Zadanie 1 | Audyt danych, usunięcie duplikatów - uniknięcie przecieku danych, plik pair_decisions.csv zawierający wynmik maualnego wybierania kopii stworzony i dodany do results|

## Licencja projektu

[GNU AFFERO GENERAL PUBLIC LICENSE Version 3, 19 November 2007](https://github.com/lindawangg/COVID-Net/blob/master/LICENSE.md)]
