# Metody uczenia maszynowego

Repozytorium z materiałami i rozwiązaniami laboratoriów z przedmiotu **Metody uczenia maszynowego** (semestr 5). Zawiera notebooki Jupyter z ćwiczeniami z klasyfikacji, preprocessingu danych, analizy obrazów oraz metod uczenia nadzorowanego i nienadzorowanego.

## Struktura projektu

```
.
├── Data/              # Zbiory danych (nie są w repozytorium — patrz sekcja „Dane”)
├── Notebooks/         # Notebooki z laboratoriów i zadań
├── pyproject.toml     # Zależności projektu (uv / pip)
└── uv.lock            # Zablokowane wersje pakietów
```

## Wymagania i uruchomienie

- **Python** ≥ 3.12
- menedżer pakietów **[uv](https://github.com/astral-sh/uv)** (zalecany) lub pip

```bash
# klonowanie repozytorium
git clone <url-repozytorium>
cd "Metody uczenia maszynowego"

# utworzenie środowiska i instalacja zależności
uv sync

# uruchomienie Jupytera
uv run jupyter notebook
# lub
uv run jupyter lab
```

Główne biblioteki: `scikit-learn`, `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-image`, `opencv-python`, `tensorflow`.

## Dane

Katalog `Data/` jest wykluczony z repozytorium (`.gitignore`) ze względu na rozmiar plików. Wiele notebooków pobiera dane automatycznie albo oczekuje ich lokalnie po ręcznym pobraniu.

| Źródło | Pliki | Uwagi |
|--------|-------|-------|
| [torus.uck.pk.edu.pl/~bar.olaf/MUM/](https://torus.uck.pk.edu.pl/~bar.olaf/MUM/) | `wine_train_big.zip`, `wine_train_small.zip`, `wine_test.csv`, `mnist_noise.zip` | Lab 4, MNIST noise |
| [github.com/olafbar/credo_files](https://github.com/olafbar/credo_files) | `images_4class.zip` | Zadania CREDO |
| Lokalnie | `lab3.csv` | Lab 3 |

Przed uruchomieniem notebooka utwórz katalog `Data/` w katalogu głównym projektu (lub jeden poziom wyżej względem `Notebooks/`, w zależności od ścieżek w danym notatniku).

## Notebooki

### Laboratoria podstawowe (MUM)

| Notebook | Temat |
|----------|-------|
| `MUM_LAB1_Preprocessing.ipynb` | Preprocessing danych — czyszczenie, imputacja braków, kodowanie zmiennych kategorycznych, skalowanie (zbiór Titanic) |
| `MUM_LAB02_ScikitLearn.ipynb` | Wprowadzenie do scikit-learn — podział train/test, KNN, regresja liniowa, drzewo decyzyjne (Iris) |
| `MUM_LAB3.ipynb` | Eksploracja i klasyfikacja danych tabelarycznych z pliku `lab3.csv` |
| `MUM_LAB04_ZADANIE_big_files.ipynb` | KNN na dużym zbiorze danych o winie (~20 mln rekordów) — preprocessing, wykrywanie data leakage, optymalizacja czasu i pamięci |

### Klasyfikatory i metryki

| Notebook | Temat |
|----------|-------|
| `MUM_LDA.ipynb` | Liniowa analiza dyskryminacyjna (LDA) — teoria i implementacja |
| `MUM_BAYES_LAB.ipynb` | Klasyfikator Naive Bayes — priorytety klas, rozkłady Gaussa, weryfikacja założeń niezależności cech |
| `MUM_ROC.ipynb` | Metryki klasyfikacji binarnej — precision, recall, krzywa ROC, dane niezbalansowane |
| `MUM_k_means.ipynb` | Klasteryzacja k-means — algorytm, zastosowania, zadania praktyczne |

### Przetwarzanie obrazów i MNIST

| Notebook | Temat |
|----------|-------|
| `MNIST_noise_lab.ipynb` | Redukcja szumu na obrazach MNIST — identyfikacja szumu Gaussa i „salt & pepper”, filtry (progowanie, Gauss, mediana), ocena przez KNN |
| `deskdewing.ipynb` | Korekcja przekrzywienia (deskewing) obrazów — wyrównanie osi obiektów przed dalszą analizą |

### Zadania CREDO (analiza obrazów cząstek)

| Notebook | Temat |
|----------|-------|
| `credo_features_lab.ipynb` | Ekstrakcja cech z obrazów — momenty Hu vs transformacja Hougha, klasyfikacja po odrzuceniu artefaktów |
| `credo_class_zad.ipynb` | Optymalizacja klasyfikatora KNN na danych z eksperymentu [CREDO](https://www.credo.science) (klasy: artefakty, linie, robaki itd.) |

## Jak korzystać z repozytorium

1. Sklonuj repozytorium i zainstaluj zależności (`uv sync`).
2. Pobierz wymagane dane do katalogu `Data/` (patrz tabela powyżej lub komórki z `wget` w notebookach).
3. Otwórz wybrany notebook w Jupyterze i ustaw kernel na środowisko z `.venv`.
4. Uruchamiaj komórki kolejno — wiele notatników zakłada wykonanie poprzednich kroków w tej samej sesji.

## Uwagi techniczne

- Notebooki używają wzorca `Path("Data")` z fallbackiem na `Path("../Data")`, aby działać zarówno z katalogu głównego, jak i z `Notebooks/`.
- Lab 4 wymaga dużo RAM i czasu — zalecany jest start od `wine_train_small.csv` (100 tys. rekordów) przed pełnym zbiorem.
- Archiwum `wine_train_big.zip` ma ok. 2,4 GB; upewnij się, że pobieranie zakończyło się w całości przed rozpakowaniem.

## Autor

Paweł Buczek — materiały z zajęć Metody uczenia maszynowego.
