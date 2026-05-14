## 📊 Diagnozowanie Chorób Serca (Heart Disease Threshold Tuning)

Projekt skupia się na zbudowaniu modelu klasyfikacyjnego (Regresja Logistyczna), który przewiduje ryzyko zawału u pacjentów. Głównym celem analitycznym nie było dążenie do maksymalnej ogólnej skuteczności (Accuracy), lecz rozwiązanie krytycznego problemu medycznego: zminimalizowanie liczby chorych diagnozowanych jako zdrowych.

🛠 **Wykorzystane technologie**

*   **Python** (Pandas) – transformacja danych medycznych, przygotowanie zmiennych zero-jedynkowych (Dummy Variables) z ominięciem pułapki współliniowości.
*   **Scikit-learn** – podział na zbiory treningowe/testowe, standaryzacja danych zapobiegająca wyciekom informacji (StandardScaler), budowa i ocena modelu Regresji Logistycznej.

📈 **Kluczowe Wnioski Analityczne:**

*   **Pułapka Paradoksu Skuteczności (Accuracy Paradox):** Udowodniono, że w medycynie wysoki wynik ogólny to za mało. Model na domyślnym progu decyzyjnym osiągał imponujące ~85% ogólnej skuteczności (Accuracy), jednak przepuszczał niemal 30% chorych pacjentów w stanie przedzawałowym (niski wskaźnik Recall).
*   **Optymalizacja Progu (Threshold Tuning):** Przejście z domyślnej funkcji `predict()` na surowe prawdopodobieństwa `predict_proba()` pozwoliło na ręczne obniżenie progu decyzyjnego do 30%. Zmuszono w ten sposób algorytm do większej "ostrożności" i wyczulenia na najdrobniejsze objawy.
*   **Kompromis Biznesowy (Trade-off):** Praktyczna demonstracja relacji między metrykami. Świadomie poświęcono część ogólnej skuteczności (spadek do 82%) i zaakceptowano wzrost liczby fałszywych alarmów (False Positives), aby drastycznie zwiększyć bezpieczeństwo i maksymalizować wykrywalność faktycznie chorych pacjentów.

📁 **Zawartość**

*   `heart-disease-classification.ipynb` - Pełny kod w Pythonie: przygotowanie danych, standaryzacja cech pacjentów, trening modelu klasyfikacyjnego, generowanie macierzy pomyłek (Confusion Matrix) oraz ręczna optymalizacja progów prawdopodobieństwa.
