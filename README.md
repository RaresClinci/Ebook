# Openbook E-Reader

## Schema bloc
``` mermaid
 flowchart TB
    USB1["USB-C"] -->|5V| Charger1["Battery Charger (MCP73832)"]
    Charger1 -->|Charging| LiPo1["LiPo Battery"]
    LiPo1 --> LDO1["3V3 LDO"]
    LiPo1 --> DC5["5V DC/DC"]

    ESP1["ESP32-C3-WROOM"]

    LDO1 -->|3.3V| ESP1
    LDO1 -->|3.3V| Display1["1.5'' E-Ink Display (200x200px)"]
    LDO1 -->|3.3V| SD1["SD Card"]
    LDO1 -->|3.3V| Temp1["Temp/RH Sensor (BME680)"]
    LDO1 -->|3.3V| BatteryGauge["Battery Fuel Gauge (MAX17048)"]
    LDO1 -->|3.3V| Buttons1["Buttons (3x)"]

    ESP1 -- SPI --> Display1
    ESP1 -- SPI --> SD1
    ESP1 -- GPIO --> Buttons1
    ESP1 -- I2C --> Temp1
    ESP1 -- I2C --> BatteryGauge
    ESP1 -- I2C --> RTC["Real Time Clock (DS3231)"]
    ESP1 -- USB --> USB1

```

## Bill of Materials

Pentru componentele care se repeta, am adaugat doar la prima aparitioe datasheetul si linkul catre site.
TP-urile le-am proiectat singur, de aceea nu au o datasheet si un link catre site.

| Name of component  | Device                                    | Check Prices                                                                 | DataSheet                                                                  |
|--------------------|-------------------------------------------|-----------------------------------------------------------------------------|----------------------------------------------------------------------------|
| BOOT_BUTTON        | BUTTON_CUSYOMV1                           | [Check Price](https://industry.panasonic.com/global/en/products/control/switch/light-touch/number/evqpuj02k)  | [DataSheet](https://industry.panasonic.com/global/en/products/control/switch/light-touch/number/evqpuj02k) |
| C1                 | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | [Check Price](https://industry.panasonic.com/global/en/products/control/switch/light-touch/number/evqpuj02k)  | [DataSheet](https://industry.panasonic.com/global/en/products/control/switch/light-touch/number/evqpuj02k) |
| C1_BAT             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C1_BAT1            | EAGLE-LTSPICE_CC0402                      | #N/A                                                                         | #N/A                                                                      |
| C1_BAT2            | EAGLE-LTSPICE_CC0402                      | #N/A                                                                         | #N/A                                                                      |
| C2                 | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C2_BAT           | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C3                 | RCL_CPOL-EUCT3528                         | #N/A                                                                         | #N/A                                                                      |
| C4                 | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C4_USB             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C5                 | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C5_USB             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C6                 | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C7                 | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C8                 | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C9                 | EAGLE-LTSPICE_CC0402                      | #N/A                                                                         | #N/A                                                                      |
| C10                | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| C10_SUPERCAP       | CPH3225A                                  | [Check Price](https://www.snapeda.com/parts/CPH3225A/Seiko+Instruments/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/CPH3225A/Seiko+Instruments/view-part/?ref=eda) |
| CHANGE_BUTTON      | BUTTON_CUSYOMV1                           | [Check Price](https://industry.panasonic.com/global/en/products/control/switch-light-touch/number/evqpuj02k)  | [DataSheet](https://industry.panasonic.com/global/en/products/control/switch-light-touch/number/evqpuj02k) |
| CHG_LED            | ADAFRUIT_LEDCHIP-LED0603                  | [Check Price](https://www.snapeda.com/parts/KP-1608SURCK/Kingbright/view-part/?ref=search&t=LED%200603) | [DataSheet](https://www.snapeda.com/parts/KP-1608SURCK/Kingbright/view-part/?ref=search&t=LED%200603) |
| C_DELAY            | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| D1                 | USBLC6-2SC6Y                              | [Check Price](https://www.snapeda.com/parts/USBLC6-2SC6Y/STMicroelectronics/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/USBLC6-2SC6Y/STMicroelectronics/view-part/?ref=eda) |
| D2                 | ESP32_WROVER_AVX---SD0805S020S1R0_AVX_... | [Check Price](https://eu.mouser.com/ProductDetail/KYOCERA-AVX/SD0805S020S1R0?qs=jCA%252BPfw4LHbpkAoSnwrdjw%3D%3D) | [DataSheet](http://datasheets.avx.com/schottky.pdf)                       |
| D3                 | MBR0530                                   | [Check Price](https://eu.mouser.com/ProductDetail/KYOCERA-AVX/SD0805S020S1R0?qs=jCA%252BPfw4LHbpkAoSnwrdjw%3D%3D) | [DataSheet](https://eu.mouser.com/ProductDetail/KYOCERA-AVX/SD0805S020S1R0?qs=jCA%252BPfw4LHbpkAoSnwrdjw%3D%3D) |
| D4                 | MBR0530                                   | [Check Price](https://www.snapeda.com/parts/MBR0530/Onsemi/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/MBR0530/Onsemi/view-part/?ref=eda) |
| D5                 | MBR0530                                   | [Check Price](https://www.snapeda.com/parts/MBR0530/Onsemi/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/MBR0530/Onsemi/view-part/?ref=eda) |
| D6                 | PGB1010603MR                              | [Check Price](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) |
| D7                 | ESP32_WROVER_AVX---SD0805S020S1R0_AVX_... | [Check Price](https://eu.mouser.com/ProductDetail/KYOCERA-AVX/SD0805S020S1R0?qs=jCA%252BPfw4LHbpkAoSnwrdjw%3D%3D) | [DataSheet](http://datasheets.avx.com/schottky.pdf)                       |
| D8                 | PGB1010603MR                              | [Check Price](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) |
| D9                 | PGB1010603MR                              | [Check Price](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) |
| D10                | PGB1010603MR                              | [Check Price](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) |
| D11                | PGB1010603MR                              | [Check Price](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) |
| D12                | PGB1010603MR                              | [Check Price](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) | [DataSheet](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) |
| EPD_C1             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C2             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C5             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C6             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C7             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C8             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C9             | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C10            | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C11            | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| EPD_C12            | ESP32_WROVER_EAGLE-LTSPICE_CC0402         | #N/A                                                                         | #N/A                                                                      |
| IC1                | BD5229G-TR                                | [Check Price](https://componentsearchengine.com/part-view/BD5229G-TR/ROHM%20Semiconductor) | [DataSheet](https://componentsearchengine.com/part-view/BD5229G-TR/ROHM%20Semiconductor) |
| IC4                | XC6220A331MR-G                            | [Check Price](https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex) | [DataSheet](https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex) |
| J1                 | FH34SRJ-24S-0.5SH_99_                     | [Check Price](https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex) | [DataSheet](https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex) |
| J2                 | SAMACSYS_PARTS_USB4110-GF-A               | [Check Price](https://componentsearchengine.com/part-view/USB4110-GF-A/GCT%20(GLOBAL%20CONNECTOR%20TECHNOLOGY) | [DataSheet](https://componentsearchengine.com/part-view/USB4110-GF-A/GCT%20(GLOBAL%20CONNECTOR%20TECHNOLOGY) |
| J3                 | QWIIC_CONNECTORJS-1MM                     | [Check Price](https://www.snapeda.com/parts/PRT-14417/SparkFun%20Electronics/view-part/?ref=search&t=qwiic%20connectpr)                                                                         | [Datasheet](https://www.snapeda.com/parts/PRT-14417/SparkFun%20Electronics/view-part/?ref=search&t=qwiic%20connectpr)                                                                        |
| J4                 | 112A-TAAR-R03_ATTEND                      | [Check Price](https://store.comet.srl.ro/Catalogue/Product/43497/)           | [DataSheet](https://store.comet.srl.ro/Catalogue/Product/43497/)          |
| L1                 | 744043680IND_4828-WE-TPC_WRE              | [Check Price](https://eu.mouser.com/ProductDetail/Wurth-Elektronik/744043680?qs=PGXP4M47uW6VkZq%252BkzjrHA%3D%3D) | [DataSheet](https://eu.mouser.com/ProductDetail/Wurth-Elektronik/744043680?qs=PGXP4M47uW6VkZq%252BkzjrHA%3D%3D) |
| PFMF.050.1         | ESP32C6_VARISTORCN1812                    | [Check Price](https://www.mouser.co.uk/ProductDetail/EPCOS-TDK/B72520T0350K062?qs=dEfas%2FXlABIszF52uu7vrg%3D%3D) | [DataSheet](https://www.mouser.co.uk/ProductDetail/EPCOS-TDK/B72520T0350K062?qs=dEfas%2FXlABIszF52uu7vrg%3D%3D) |
| Q1                 | ESP32_WROVER_SPARKFUN-DISCRETESEMI_MOSFET_... | [Check Price](https://componentsearchengine.com/part-view/DMG2305UX-7/Diodes%20Incorporated) | [DataSheet](https://componentsearchengine.com/part-view/DMG2305UX-7/Diodes%20Incorporated) |
| Q2                 | ESP32_WROVER_SPARKFUN-DISCRETESEMI_MOSFET_... | #N/A                                                                         | #N/A                                                                      |
| Q3                 | D8                                        | [Check Price](https://componentsearchengine.com/part-view/PGB1010603MR/Littelfuse) | [DataSheet](https://componentsearchengine.com/part-view/PGB1010603MR/Littelfuse) |
| Q4                 | Q2_TS-B2_REACHPACK                        | #N/A                                                                         | #N/A                                                                      |
| SJ1                 | SJ                                        | [Check Price](https://grabcad.com/library/solder-jumpers-1) | [DataSheet](https://grabcad.com/library/solder-jumpers-1) |                                                                  |

## Descriere detaliată a funcționalității hardware

### 1. Microcontroller – ESP32-C6
Dispozitivul se bazează pe microcontroller-ul**ESP32-C6-WROOM-1**, bazat pe un nucleu **RISC-V pe 32 de biți**, cu frecvențe de lucru de până la **160 MHz**.

- **Memorie**: 512 KB de SRAM intern și **8 MB flash extern** (W25Q512JVEIQ).
- **Conectivitate**: Wi-Fi 6, Bluetooth 5 LE, USB 2.0
- **Periferice**: suport pentru SPI, I²C, UART și multiple GPIO-uri.
- **Moduri de consum redus**: suportă sleep și deep sleep, ideale pentru dispozitive portabile alimentate cu baterie.

### 2. Afișaj E-Ink
**E-Ink de 7.5" (800x480px)** – Waveshare (sau echivalent) cu rezoluție 800×480

**Interfață**: 4-wire SPI + pini de control (CS, DC, RST, BUSY).  
**Consum**: extrem de redus în regim static; doar în timpul reîmprospătării imaginea consumul crește la ~15–25mA.

 **Avantaj**: Afișajele E-Ink păstrează imaginea fără consum de curent, ceea ce le face perfecte pentru aplicații de tip e-reader.

### 3. Senzor de Mediu – BME680
Senzorul integrează măsurători de **temperatură**, **umiditate**, **presiune atmosferică** și **calitate a aerului (VOC/eCO₂)**.

- **Interfață**: I²C la 400 kHz.
- **Consum**: ~2.1µA în standby, până la câțiva mA în timpul citirilor.

 **BME680** este o alegere excelenta datorita capacitatii sale de a integra multiple tipuri de masuratori intr-un singur cip

### 4. Managementul energiei
- **Baterie Li-Po 3.7V, 2500mAh** – oferă autonomie extinsă.
- **Circuit de încărcare**: MCP73831, conectat la USB-C, permite încărcare cu până la **1A**.
- **Fuel Gauge**: MAX17048 – monitorizează starea bateriei prin I²C (tensiune, încărcare, alertă descărcare).
- **LDO**: XC6220A331MR-G – asigură **tensiune stabilă de 3.3V** pentru toate componentele critice.

### 5. Interacțiune – Butoane (3x)
Dispozitivul include **trei butoane tactile** pentru navigare, selectare și întoarcere pagină. Fiecare este conectat la un GPIO și poate avea debouncing hardware (rezistor + condensator) sau software, pentru evitarea semnalelor false.

### 6. Port USB-C
- **Roluri**: încărcarea bateriei, transfer de date (USB 2.0), și update de firmware (via bootloader sau OTA).
- **Protecție**: ESD (ex: USBLC6-2SC6Y), rezistențe de terminare conforme cu specificațiile USB-C.

### 7. Conector Qwiic (I²C)
Conector standard cu 4 pini (VCC, GND, SDA, SCL) pentru atașarea rapidă a senzorilor/modulor I²C, ideal în extensii și prototipare.

### 8. Card MicroSD(112A-TAAR-R03)
- **Conector dedicat**: pentru log-uri, e-book-uri sau update-uri firmware.
- **Interfață**: Poate fi SD (1-bit / 4-bit) sau SPI, în funcție de configurația firmware-ului.

### 9. Ceas de timp real – RTC DS3231
- **Precizie ridicată**.
- **Backup**: cu baterie sau supercondensator.
- **Comunicare**: I²C, împreună cu ceilalți senzori.

### 10. Memorie Flash externă – W25Q512JVEIQ
- **Interfață**: quad SPI – pentru încărcare rapidă de date și firmware.
- Utilizată pentru stocarea aplicațiilor, imaginilor sau fișierelor mari (ex: e-book-uri).

---

### Interfețele utilizate

| Interfață | Componente conectate |
|----------|------------------------|
| **SPI**  | Afișaj E-Ink, memorie flash externă, card SD |
| **I²C**  | BME680, MAX17048 (fuel gauge), RTC DS3231, conector Qwiic |
| **GPIO** | Butoane, control display (RST, BUSY etc.) |
| **USB**  | Alimentare și date (USB-C) |

---

### Estimare consum energetic

| Componentă              | Consum tipic                     |
|-------------------------|----------------------------------|
| ESP32 (activ)           | ~80 mA (Wi-Fi) / <10 mA (idle)   |
| E-Ink (refresh)         | ~15–25 mA                        |
| BME680                  | ~3.6 mA (peak) / 2.1 µA (sleep)  |
| MAX17048 (Fuel Gauge)   | ~50 µA                           |
| DS3231 (RTC)            | ~3.5 mA (activ) / <1 µA (backup) |
| Total (deep sleep)      | ~50–100 µA                       |
| Total (activ cu Wi-Fi)  | ~100–150 mA                      |

> Cu o baterie de **2500mAh**, în regim normal de utilizare (afișaj static, deep sleep majoritatea timpului), autonomia poate atinge **câteva săptămâni**.

## Alocarea pinilor pentru ESP32-C6

| Pin ESP32-C6  | Componentă / Semnal                       | Descriere                                           |
|---------------|-------------------------------------------|-----------------------------------------------------|
| GPIO1         | I²C SDA (BME680, MAX17048, DS3231, Qwiic) | Linie de date partajată pentru toți senzorii(+ RTC) conectați pe magistrala I²C. |
| GPIO2         | I²C SCL (BME680, MAX17048, DS3231, Qwiic) | Linie de clock pentru sincronizarea comunicației I²C. |
| GPIO5         | SPI MISO (E-Paper)                        | Recepție date de la afișajul E-Paper.              |
| GPIO6         | SPI MOSI (E-Paper)                        | Transmitere date către afișajul E-Paper.           |
| GPIO7         | SPI CLK (E-Paper)                         | Semnal de clock pentru interfața SPI a ecranului.  |
| GPIO8         | SPI CS (E-Paper)                          | Chip Select pentru e-paper.   |
| GPIO9         | E-Paper DC (Data/Command)                 | Selectează între transmiterea de date sau comenzi către afișaj. |
| GPIO10        | E-Paper RST                               | Reset hardware al afișajului.                      |
| GPIO11        | E-Paper BUSY                              | Indică dacă afișajul este ocupat cu o operație.    |
| GPIO12        | Button #1                                 | Buton de control (ex. „Pagina următoare”).         |
| GPIO13        | Button #2                                 | Buton de control (ex. „Pagina anterioară”).        |
| GPIO14        | Button #3                                 | Buton de control (ex. „Meniu” sau „Select”).       |
| GPIO15        | MAX17048 ALERT (opțional)                 | Semnal de alertă de la senzorul de baterie (low battery). |
| GPIO16        | USB D+ (intern la USB PHY)                | Semnal diferențial pozitiv pentru conexiunea USB 2.0. |
| GPIO17        | USB D- (intern la USB PHY)                | Semnal diferențial negativ pentru conexiunea USB 2.0. |
| GPIO18        | LED de status (opțional)                  | LED pentru semnalizare stări (Wi-Fi, încărcare etc.). |
| GPIO19        | SD Card CS (opțional)                     | Chip Select pentru cardul microSD (SPI).           |
| GPIO20        | SD Card MISO (opțional)                   | Linie de citire date de la cardul microSD.         |
| GPIO21        | SD Card MOSI (opțional)                   | Linie de scriere date către cardul microSD.        |
| GPIO4         | SD Card CLK (opțional)                    | Linie de clock pentru comunicația SPI cu cardul SD.|

## Note
- am adaugat la partea de PCB 2D niste masuratori in plus pentru claritate
- am pozitionat TP-urile in cel mai apropiat loc de componentele conectate
- am mai adaugat pe placa o zona unde poate fi scris numarul de serie al placii si versiunea ei(probabil va deveni Openbook v1.2 dupa feedback - UPDATE: chiar a devenit)
- pentru baterie, am folosit un paralelipiped cu dimensiunile maxime din datasheet
- la partea de PCB, am aprobat 2 erori de gauri de la o componenta si o eroare de Airwire la componenta J4, are 9 grounduri puse intr-un grid 3x3 si cel din mijloc nu e accesibil

## Concluzii
A fost un proiect destul de solicitant, dar cu multa munca am reusit sa il duc pana la capat. Am luat in considerare majoritatea indicatiilor si sunt deschis sa fac imbunatatiri pe urma feedbackului.
