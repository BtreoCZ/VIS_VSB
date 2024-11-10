# Technická specifikace: Kino Rezervační Systém

## 1. Architektura
- **Backend**: ASP.NET Core (C#) pro tvorbu API a backend logiky
- **Databáze**: SQLite pro relační data, vhodná pro menší objem dat a jednodušší aplikace
- **Frontend**: Blazor pro webové aplikace, Xamarin/MAUI pro mobilní aplikace (iOS a Android)
- **Autentifikace**: OAuth 2.0, JWT
- **Platby**: Možnosti integrace s platebními branami, jako je PayPal SDK nebo Stripe API, pro bezpečné online platby

![Popis obrázku](C:\Users\judis\OneDrive - VSB-TUO\Plocha\VIS\mode_diagram)

## 2. Odhad velikosti entit a jejich množství

| **Entita**       | **Odhadovaná velikost na záznam** | **Odhadovaný počet záznamů** | **Celková velikost dat** |
|------------------|-----------------------------------|------------------------------|--------------------------|
| **Rezervace**    | 100 KB                            | 500 000 - 1 000 000         | 50 GB - 100 GB           |
| **Platba**       | 50 KB                             | 500 000 - 1 000 000         | 25 GB - 50 GB            |
| **Kino**         | 200 KB                            | 100 - 500                   | 20 MB - 100 MB           |
| **Film**         | 300 KB                            | 1 000                       | 300 MB                   |
| **Promítání**    | 100 KB                            | 10 000                      | 1 GB                     |
| **Sedadlo**      | 10 KB                             | 10 000 - 20 000             | 100 MB - 200 MB          |
| **Zákazník**     | 100 KB                            | Max 100 000                 | 10 GB                    |

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
- **Databáze**: SQLite pro relační entity.

## 7. Technologie a platformy
- **Backend**: ASP.NET Core (C#) pro tvorbu API a backend logiky
- **Frontend**: Blazor pro web, Xamarin/MAUI pro mobilní aplikace
- **Databáze**: SQLite pro relační data
- **Platby**: Stripe API nebo PayPal SDK pro bezpečné platby.
- **Cílené platformy**: 
  - **Web**: Pro přístup přes prohlížeče (pro desktop a mobilní zařízení).
  - **Mobilní aplikace**: Xamarin/MAUI pro iOS/Android.
