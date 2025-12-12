# Arkanoid PyGame

> Klasyczna gra zręcznościowa typu Arkanoid zaimplementowana w Pythonie z wykorzystaniem silnika PyGame, obsługująca fizykę odbić, poziomy trudności i system żyć.

![Python](https://img.shields.io/badge/python-3.x-blue.svg)
![PyGame](https://img.shields.io/badge/pygame-2.x-green.svg)

## 📝 O projekcie
Jest to moja implementacja kultowej gry Arkanoid, stworzona w celu zgłębienia tajników programowania gier i symulacji fizyki w czasie rzeczywistym. Projekt skupia się na **programowaniu obiektowym** (OOP) oraz manualnej obsłudze kolizji bez polegania wyłącznie na wbudowanych, prostych metodach silnika. Gra oferuje system progresji poziomów oraz klocki o różnej wytrzymałości.

## 🛠 Technologia (Tech Stack)
Projekt został napisany w czystym Pythonie z użyciem biblioteki PyGame do renderingu i obsługi wejścia.
* **Język:** Python 3
* **Silnik:** PyGame (obsługa Sprite'ów, pętli gry, eventów)
* **Matematyka:** `pygame.math.Vector2` (obliczenia wektorowe dla ruchu piłki)
* **Zarządzanie stanem:** Klasy i dziedziczenie (`pygame.sprite.Sprite`)

## ✨ Główne funkcjonalności
* **System poziomów:** Mapy klocków są definiowane za pomocą macierzy (listy list), co pozwala na łatwe projektowanie nowych etapów (obecnie zaimplementowane 3 poziomy).
* **Zaawansowana fizyka paletki:** Ruch piłki po odbiciu zależy nie tylko od kąta padania, ale też od pędu paletki (dodawanie wektora ruchu gracza do wektora piłki).
* **Mechanika klocków:** Klocki posiadają "punkty życia" (1-3). Ich kolor zmienia się dynamicznie w zależności od pozostałego zdrowia, wykorzystując `pygame.BLEND_ADD`.
* **Wykrywanie kolizji:** Własna implementacja logiki odbić (rozróżnianie uderzeń w bok vs. góra/dół klocka) dla zapewnienia precyzyjnej rozgrywki.

## 💡 Wyzwania i rozwiązania
W tym projekcie największym wyzwaniem była **precyzyjna detekcja kolizji**.
* **Problem:** Standardowe `rect.colliderect` nie informuje, z której strony nastąpiło zderzenie, co powodowało "wpadanie" piłki w klocki lub błędne odbicia.
* **Rozwiązanie:** Zaimplementowałem funkcję obliczającą dystans między środkiem piłki a krawędziami klocka (`dystans_x` vs `dystans_y`). Dzięki temu program wie, czy odwrócić wektor X czy Y, co eliminuje błędy fizyki.

Dodatkowo, zastosowałem dziedziczenie z `pygame.sprite.Sprite` i wykorzystałem `pygame.sprite.Group` do optymalnego zarządzania i renderowania wielu obiektów jednocześnie.

## 🚀 Jak uruchomić lokalnie

Wymagane jest posiadanie zainstalowanego Pythona oraz folderu `images/` z grafikami (`background.png`, `pad.png`, `ball.png`, `brick.png`).

```bash
# Instalacja biblioteki PyGame
pip install pygame

# Uruchomienie gry
python projekt.py
