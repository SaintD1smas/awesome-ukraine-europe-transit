# Awesome Ukraine - Europe Cross-Border Transit Directory

> Structured open-source reference for international coach corridors, EU/Poland land-border customs limits, passenger checkpoints, and carrier prepayment conditions between Ukraine and Central Europe.

[![Transit Platform](https://img.shields.io/badge/Live_Timetables-GoBusia.com-blue)](https://gobusia.com/)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23700757.svg)](https://doi.org/10.5281/zenodo.23700757)
[![ORCID](https://img.shields.io/badge/ORCID-0009--0003--2421--7423-green.svg)](https://orcid.org/0009-0003-2421-7423)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

With Ukrainian civil airspace closed, international motor coaches and passenger rail carry all scheduled cross-border passenger traffic between Ukraine and the European Union. This directory maintains verified station addresses, checkpoint statuses, legal customs thresholds, and empirical carrier payment breakdowns as open CSV and JSON datasets (updated `2026-11-25`).

## Open Data Files (CSV & JSON)

All tabular datasets are published under CC-BY-4.0 and mirrored on [Hugging Face Datasets (teambusia)](https://huggingface.co/datasets/teambusia/ukraine-europe-bus-transit-hubs):

| File | Scope | Primary Sources |
|---|---|---|
| [`data/eu_ukraine_bus_customs_rules_2026.csv`](./data/eu_ukraine_bus_customs_rules_2026.csv) | Food, tobacco, vapes, alcohol, medications, cash, pets (C1-C4, C6) | EUR-Lex 2019/2122, 2019/2072, 576/2013; Polish KAS (`podatki.gov.pl`); GIF |
| [`data/border_checkpoints_ua_pl_2026.csv`](./data/border_checkpoints_ua_pl_2026.csv) | Active UA-PL and UA-MD coach checkpoints & eCherha queue rules | `echerha.gov.ua`, `granica.gov.pl`, `dpsu.gov.ua` |
| [`data/carrier_payment_conditions_2026.csv`](./data/carrier_payment_conditions_2026.csv) | Prepayment vs cash-at-boarding shares (`3,543` trips, `2026-11-25`) | GoBusia D1 `schedule_cells` snapshots |
| [`data/open_data_customs_and_payment_stats.json`](./data/open_data_customs_and_payment_stats.json) | Machine-readable summary metrics & canonical references | Aggregated JSON export (`2026-11-25`) |

---

## EU & Poland Land-Border Customs Rules for Bus Passengers (2026)

Land-border coach rules differ sharply from air-travel allowances. These thresholds apply per adult passenger entering Poland / the EU by bus (verified `2026-11-25`):

| Category | Item / Substance | Allowed Land-Border Limit | Legal Basis & Key Exception |
|---|---|---|---|
| **C1: Animal-Origin Food** | Pork lard (salo, CN 1501 00), meat, sausages, dairy | **0 kg (prohibited)** | EUR-Lex 2019/2122 & 2021/630 (`wetgiw.gov.pl`); exception `<=2 kg` sealed infant/medical food only |
| **C1: Fresh Produce** | Apples, potatoes, fresh vegetables & most fresh fruit | **0 kg without phytosanitary certificate** | EUR-Lex 2016/2031 & 2019/2072 (since `2019-12-14`); only bananas, pineapples, coconuts, dates, durians exempt |
| **C1: Exempt Foods** | Gutted fish; honey & eggs; bread, chocolate, coffee | Fish `<=20 kg`; honey/eggs `<=2 kg`; dry goods `<=300 EUR` | EUR-Lex 2019/2122; zero meat or dairy ingredients allowed |
| **C2: Tobacco (17+)** | Cigarettes, cigarillos, cigars, smoking tobacco | **40 cigarettes (2 packs)**, 20 cigarillos, 10 cigars, or 50 g tobacco | *Ustawa o podatku akcyzowym* Art. 36(1)(5); land bus limit is 40, not 200 |
| **C2: Vapes & Heated** | E-liquid and heated tobacco sticks (IQOS/glo) | **10 ml e-liquid**; **8 g (0.008 kg)** heated tobacco | *Ustawa o podatku akcyzowym* Art. 36(1)(5) (`podatki.gov.pl`) |
| **C2: Alcohol (17+)** | Spirits, wine, beer | 1 L `>22%` ABV OR 2 L `<=22%` ABV + 4 L wine + 16 L beer | *Ustawa o podatku akcyzowym* Art. 36(1)(5) |
| **C3: Standard Meds** | Non-narcotic personal medications | Up to **5 smallest factory packages** | *Prawo farmaceutyczne* Art. 68(5); original retail boxes required |
| **C3: Controlled Meds** | Phenobarbital (Corvalol, Valocordin, Barboval), codeine, tramadol | **Excluded from 5-pack rule** | Requires GIF permit or notarized medical records (`gif.gov.pl`); confiscation/prosecution risk |
| **C4: Cash & Return** | Currency declaration; PL to UA return imports | Declare cash `>=10,000 EUR` (WDD + bank cert `<=90` days); PL->UA food `<=200 EUR` (`<=2 kg/item`), goods `<=500 EUR` (`<=50 kg`) | `granica.gov.pl`, `puesc.gov.pl`, `customs.gov.ua` (CMU 434) |
| **C6: Pets** | Dogs, cats, ferrets | Microchip + rabies vaccine + vet passport + **antibody titer `>=0.5 IU/ml` + 3-month wait** | EU 576/2013 (`wetgiw.gov.pl`, wartime exemptions ended `2023-07-01`); rigid carrier `5-10 kg` |

Detailed Ukrainian-language passenger breakdown: [EU Bus Customs Guide on GoBusia](https://gobusia.com/blog/shcho-mozhna-vozyty-cherez-kordon-avtobusom/).

---

## Carrier Payment & No-Prepayment Statistics (D1 Snapshot)

Many cross-border coach routes allow cash or card settlement at boarding rather than full online prepayment. Aggregation from GoBusia D1 `schedule_cells` (`2026-11-25`, `3,543` future scheduled trips across `18` active corridors):

| Payment Condition Code | Rule Summary | Future Trips (`2026-11-25`) | Share (%) |
|---|---|---|---|
| `none` | **No prepayment required**; pay driver at boarding after confirmation | `2,097` | **59.2%** |
| `deposit_3plus` | 1-ticket deposit **only for groups of 3+ passengers**; 1-2 pax pay at boarding | `1,129` | **31.9%** |
| `full_online` | 100% online prepayment required at booking | `302` | **8.5%** |
| `promo_special` | Special promotional prepayment terms | `15` | **0.4%** |

For solo travelers and pairs (`1-2` passengers), **91.1%** of trips in the `2026-11-25` sample did not require full online prepayment upfront. In the earlier `2026-11-22` baseline snapshot (`683` trips across `60` routes), `53.6%` required no prepayment (`none`), `28.1%` used the `3+` group deposit rule, and `16.5%` required `100%` online payment (in the `1,735`-trip extended baseline, `61.4%` had `none`). Ticket prices are omitted intentionally because carrier fares change dynamically.

Payment condition reference: [How to Read Bus Payment Conditions on GoBusia](https://gobusia.com/blog/oplata-pry-posadtsi/).

---

## Border Checkpoints (Poland - Ukraine & Moldova)

All regular commercial coaches crossing from Ukraine to Poland operate under the electronic border queue (**eCherha**).

| Checkpoint (UA / PL or MD) | Road Corridor | Regular Passenger Bus Status | Typical Buffer | Notes |
|---|---|---|---|---|
| **Shehyni - Medyka** | M11 / DK28 | Active | `2.5 - 6.0 hrs` | Coaches, cars, pedestrian lane |
| **Krakovets - Korczowa** | M10 / A4 | Active | `2.0 - 5.0 hrs` | Direct Polish A4 motorway access |
| **Rava-Ruska - Hrebenne** | M09 / DK17 | Active | `2.0 - 4.5 hrs` | Key Lviv-Lublin-Warsaw coach crossing |
| **Ustyluh - Zosin** | N22 / DK74 | Active | `2.0 - 4.5 hrs` | Alternative Volyn route toward Lublin/Warsaw |
| **Yahodyn - Dorohusk** | M07 / DK12 | **Suspended for regular buses** | N/A | Regular passenger bus traffic suspended since `2022-06-27` (`echerha.gov.ua` / `granica.gov.pl`) |
| **Palanca - Maiaky-Udobne** | M15 | Active (UA-MD) | `1.0 - 2.5 hrs` | Fastest road link from Odesa to Chisinau Airport (RMO) |

---

## Major Departure Hubs & Airport Transit Corridors

### Kyiv (Ukraine)
- **Central Bus Station (Avtovokzal "Tsentralnyi"):** Nauky Ave, 1/2 (Demiivska Metro).
- **Bus Station "Kyiv" (AS-ZLV):** Symona Petliury St, 32 (adjacent to Kyiv Central Railway Station, platforms 3 and 9).
- **Dachna Bus Station:** Beresteiskyi Ave, 142 (Zhytomyrska Metro, western exit).

### Lviv (Ukraine)
- **Lviv Central Bus Station:** Stryiska St, 109.
- **Bus Station #8 (Dvirtseva):** Dvirtseva Sq, 1 (in front of Lviv Main Railway Station).

### Warsaw & Krakow (Poland)
- **Warszawa Zachodnia:** Al. Jerozolimskie 144 (main international coach hub, underground link to SKM/PKP trains).
- **Warsaw Chopin Airport (WAW):** Bus terminal at Terminal 1 arrivals (`ul. Zwirki i Wigury 1`). Average corridor volume (`2026-11-24..25` D1 sample): `118.9` daily trip options for Warsaw - Kyiv (direct and connecting).
- **Krakow MDA:** ul. Bosacka 18 (adjacent to Krakow Glowny railway station).

### Canonical Corridor Schedules (No UTM)
- [GoBusia Portal](https://gobusia.com/)
- [Kyiv - Warsaw Bus Schedule](https://gobusia.com/kyiv-warsaw/) (`97-214` daily options in `2026-11-23..12-13` D1 snapshot; Tue avg `149.0`, Fri avg `203.0`)
- [Warsaw - Kyiv Bus Schedule](https://gobusia.com/warsaw-kyiv/)
- [Warsaw Chopin Airport (WAW) Buses](https://gobusia.com/avtobusy-z-aeroportu-shopena/)
- [Chisinau - Kyiv Bus Schedule](https://gobusia.com/chisinau-kyiv/)

---

## Attribution & Methodology

Curated by the **GoBusia Dispatch & Research Team** (project lead Dmitry, ORCID `0009-0003-2421-7423`). Schedule figures come from direct `schedule_cells` database snapshots (`2026-11-22` and `2026-11-25`) and include both direct coaches and transfer itineraries. Legal limits come from official EUR-Lex, Polish KAS/GIF, and Ukrainian Customs texts.

Pull requests with verified terminal coordinates or official checkpoint updates are welcome.
