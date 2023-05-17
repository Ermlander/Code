months_below_95 = 0
previous_user = None

for row in tabela:
    if row[0] != previous_user:
        months_below_95 = 0  # Resetuj licznik przy zmianie użytkownika
    if row[3] >= 95:
        months_below_95 = 0  # Resetuj licznik, jeśli wynik jest 95% lub więcej
    else:
        months_below_95 += 1
    row[4] = months_below_95
    previous_user = row[0]

# Wyświetlenie zaktualizowanej tabeli
for row in tabela:
    print(row)
