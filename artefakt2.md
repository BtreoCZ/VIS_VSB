
![usecase](https://github.com/user-attachments/assets/5eef73c1-b5f2-402e-b507-29628cc48052)


# Use Cases

## Název: Smazání členské karty
**Aktéři:** Manažer, Správce  
**Vstupní podmínky:** Zákazník musí vlastnit platnou členskou kartu  
**Spouštěč:** Uživatelská akce

### Úspěšný scénář:
1. Manažer vybere okno „Odstranit kartu“.
2. Otevře se okno, kde manažer musí napsat nebo naskenovat číslo karty.
3. Manažer potvrdí odstranění karty.
4. Karta se úspěšně odstraní a vypíše se hláška „Karta byla odstraněna“.

### Alternativní scénář:
1. Při načtení čísla karty se zjistí, že karta neexistuje.
2. Aplikace vypíše chybovou hlášku.
3. Aplikace se vrátí na okno pro načtení čísla karty.

---

## Název: Vytvoření zaměstnance
**Aktéři:** Správce  
**Vstupní podmínky:** Daný zaměstnanec nesmí už existovat  
**Spouštěč:** Uživatelská akce

### Úspěšný scénář:
1. Správce vybere okno „Přidat zaměstnance“.
2. Otevře se okno, kde správce musí vypsat údaje o zaměstnanci a jeho pozici.
3. Správce potvrdí vytvoření nového zaměstnance.
4. Karta se úspěšně zavře a vypíše se hláška „Zaměstnanec vytvořen“.

### Alternativní scénář:
1. Při vypisování údajů systém zjistí, že zaměstnanec už existuje.
2. Systém vypíše chybovou hlášku.
3. Systém se vrátí na okno pro zapisování údajů o zaměstnanci.

---

## Název: Vytvoření rezervace
**Aktéři:** Zaměstnanec, Manažer  
**Vstupní podmínky:** Musí být platný termín/čas pro daný film  
**Spouštěč:** Uživatelská akce

### Úspěšný scénář:
1. Zaměstnanec vybere okno „Vytvořit rezervaci“.
2. Otevře se okno, kde zaměstnanec musí vyplnit údaje o zákazníkovi potřebné k rezervaci a vybrat daná místa.
3. Zaměstnanec potvrdí výběr rezervace.
4. Karta se úspěšně zavře a vypíše se hláška „Rezervace úspěšně vytvořena“.

### Alternativní scénář:
1. Zaměstnanec nevypíše potřebné informace pro rezervaci.
2. Systém vypíše „Prosím vyplňte všechny povinné informace“.
3. Systém se vrátí na okno pro vypisování údajů o rezervaci s už vyplněnými údaji.


# Aktivitní diagram

   ![image](https://github.com/user-attachments/assets/25fd7ecd-d374-4372-9579-f06693430207)

