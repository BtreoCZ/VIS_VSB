
# Technická specifikace: Kino Rezervační Systém

## 1. Architektura
- **Frontend**: React.js (pro webové aplikace), React Native (pro mobilní aplikace)
- **Backend**: Node.js/Express, REST API
- **Databáze**: MySQL/PostgreSQL pro relační data, S3 nebo jiný blob storage pro přílohy (např. obrázky lístků)
- **Autentifikace**: OAuth 2.0, JWT
- **Platby**: Stripe API pro online platby

## 2. Odhad velikosti entit a jejich množství

| **Entita**       | **Odhadovaná velikost na záznam** | **Odhadovaný počet záznamů** | **Celková velikost dat** |
|------------------|-----------------------------------|------------------------------|--------------------------|
| **Přílohy**      | 1-5 MB                            | 100 000 - 1 000 000           | 100 GB - 5 TB            |
| **Uživatelé**    | 500 KB                            | Max 100 000                   | 50 GB                    |
| **Filmy**        | 200 KB                            | 1 000                         | 200 MB                   |
| **Rezervace**    | 100 KB                            | 500 000 - 1 000 000           | 50 GB - 100 GB           |
| **Členství**     | 50 KB                             | 50 000                        | 2.5 GB                   |

## 3. Odhad počtu uživatelů současně pracujících se systémem
- **Průměrný počet**: 500 uživatelů současně
- **Špičkový počet (peak)**: 5 000 uživatelů během populárních filmů a premiér

## 4. Typy interakcí uživatelů se systémem a jejich náročnost
- **Registrace/Přihlášení**: Nízká výpočetní náročnost, vyžaduje více I/O operací pro databázi a autentifikaci.
- **Vyhledávání filmů a sedadel**: Nízká až střední náročnost. Více čtecích operací na databázi (dotazy pro filmové tituly, dostupná sedadla).
- **Rezervace vstupenek**: Vysoká I/O operace (zápis do databáze), záleží na synchronizaci rezervací a plateb.
- **Platby**: Střední výpočetní náročnost. Integrace s platební bránou (Stripe API) přináší určité latence, zajištění bezpečnosti plateb.

## 5. Výpočetní náročnost a operace
- **Výpočetně náročné operace**: 
  - Zpracování a potvrzování plateb.
  - Synchronizace dostupných sedadel v reálném čase během rezervací.
  - Správa členství a slev (kalkulace na úrovni profilu uživatele).
  
- **I/O operace**: 
  - Čtení/zápis při vytváření rezervací, ukládání filmových příloh (plakáty, QR kódy lístků).
  - Platby přes externí bránu (Stripe API) s vysoce zabezpečeným přístupem.

## 6. Rozložení systému
- **Microservices**: Každá hlavní funkce (např. správa uživatelů, platby, rezervace) bude implementována jako nezávislá služba pro snadnější škálování.
- **Load Balancer**: NGINX/AWS ELB pro rozložení zátěže mezi servery.
- **Databáze**: SQL databáze (MySQL/PostgreSQL) pro relační data a blob storage pro velké přílohy.

## 7. Technologie a platformy
- **Backend**: Node.js/Express (pro REST API)
- **Frontend**: React.js pro web, React Native pro mobilní aplikace
- **Databáze**: MySQL nebo PostgreSQL pro vztahové entity, S3 nebo Azure Blob Storage pro přílohy.
- **Platby**: Stripe API pro bezpečné platby.
- **Cílené platformy**: 
  - **Web**: Pro přístup přes prohlížeče (pro desktop a mobilní zařízení).
  - **Mobilní aplikace**: React Native pro iOS/Android.
