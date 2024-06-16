# Prosta Aplikacja w Pythonie z Automatyzacją Procesów za Pomocą Makefile

Jest to prosta aplikacja w Pythonie z zautomatyzowanymi procesami przy użyciu Makefile.

## Kroki do Uruchomienia Aplikacji

1. **Instalacja Zależności**:
    ```sh
    make install
    ```
    Uwaga: Dla tej prostej aplikacji w Pythonie, nie ma zależności do zainstalowania.

2. **Uruchamianie Testów Jednostkowych**:
    ```sh
    make test
    ```

3. **Uruchamianie Aplikacji**:
    ```sh
    make run
    ```

## Opis Plików

- **app.py**: Główny plik aplikacji zawierający funkcję `hello`.
- **test_app.py**: Testy jednostkowe dla aplikacji przy użyciu modułu `unittest`.
- **Makefile**: Zawiera reguły automatyzacji dla instalacji zależności, uruchamiania testów i uruchamiania aplikacji.
- **README.md**: Dokumentacja projektu i instrukcje dotyczące użycia Makefile.

## Uruchamianie Makefile

Upewnij się, że masz zainstalowany `make` na swoim systemie. Otwórz terminal i przejdź do katalogu projektu. Następnie możesz uruchomić następujące polecenia:

- `make install`: Instalacja zależności (jeśli istnieją).
- `make test`: Uruchamianie testów jednostkowych.
- `make run`: Uruchamianie aplikacji.
