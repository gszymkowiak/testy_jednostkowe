# Microsoft Native Unit Test Framework for C++

Przykład wykorzystania frameworka testów jednostkowych Microsoftu dla natywnego C++ w Visual Studio.

---

# Wymagania

- Visual Studio 2022
- Pakiet **Desktop development with C++**
- Projekt typu:

```text
Native Unit Test Project
```

---

# Tworzenie projektu testowego

## 1. Utwórz nowy projekt

W Visual Studio wybierz:

```text
File → New → Project
```

Następnie wybierz:

```text
Native Unit Test Project
```

---

# Struktura projektu

Przykładowy projekt zawiera:

```text
Project
│
├── pch.h
├── pch.cpp
├── unittest1.cpp
```

---

# Podstawowy test jednostkowy

## Przykład funkcji

```cpp
int Add(int a, int b)
{
    return a + b;
}
```

---

## Przykład testu

```cpp
#include "pch.h"
#include "CppUnitTest.h"

using namespace Microsoft::VisualStudio::CppUnitTestFramework;

namespace UnitTests
{
    TEST_CLASS(CalculatorTests)
    {
    public:

        TEST_METHOD(AdditionTest)
        {
            int result = 2 + 3;

            Assert::AreEqual(5, result);
        }
    };
}
```

---

# Elementy frameworka

## TEST_CLASS

Definiuje klasę zawierającą testy.

```cpp
TEST_CLASS(CalculatorTests)
```

---

## TEST_METHOD

Definiuje pojedynczy test.

```cpp
TEST_METHOD(AdditionTest)
```

---

## Assert

Służy do sprawdzania warunków testowych.

### Przykłady

```cpp
Assert::AreEqual(5, value);
Assert::IsTrue(x > 0);
Assert::IsFalse(flag);
Assert::IsNull(ptr);
Assert::IsNotNull(ptr);
```

---

# Testowanie własnych funkcji

## Kod aplikacji

```cpp
int Multiply(int a, int b)
{
    return a * b;
}
```

---

## Kod testu

```cpp
TEST_METHOD(MultiplicationTest)
{
    int result = Multiply(4, 5);

    Assert::AreEqual(20, result);
}
```

---

# Uruchamianie testów

## Test Explorer

W Visual Studio:

```text
Test → Test Explorer
```

---

## Uruchomienie wszystkich testów

```text
Test → Run All Tests
```

---

# Wyniki testów

Visual Studio pokazuje:

- testy zakończone sukcesem,
- testy zakończone błędem,
- komunikaty błędów,
- czas wykonania.

---

# Przykład nieudanego testu

```cpp
TEST_METHOD(FailingTest)
{
    Assert::AreEqual(10, 5);
}
```

Wynik:

```text
Assert failed. Expected:<10>. Actual:<5>.
```

---

# Dobre praktyki

- jeden test powinien sprawdzać jedną rzecz,
- nazwy testów powinny być czytelne,
- testy powinny być niezależne,
- testy powinny być szybkie,
- należy unikać zależności od plików i środowiska.

---

# Typowy schemat testu

## Arrange

Przygotowanie danych.

## Act

Wywołanie testowanej funkcji.

## Assert

Sprawdzenie wyniku.

---

## Przykład

```cpp
TEST_METHOD(DivisionTest)
{
    // Arrange
    int a = 10;
    int b = 2;

    // Act
    int result = a / b;

    // Assert
    Assert::AreEqual(5, result);
}
```

---

# Namespace frameworka

```cpp
using namespace Microsoft::VisualStudio::CppUnitTestFramework;
```

Framework znajduje się w:

```cpp
Microsoft::VisualStudio::CppUnitTestFramework
```

---

# Podsumowanie

Microsoft Native Unit Test Framework umożliwia:

- automatyczne testowanie kodu C++,
- integrację z Visual Studio,
- szybkie wykrywanie błędów,
- bezpieczną refaktoryzację kodu,
- budowę testów regresyjnych.

Framework jest natywnym odpowiednikiem MSTest dla języka C++.

