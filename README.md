# 📦 Sortieranlage mit Förderband & 3 Ausschiebern  
### Grundkurs SPS – Aufgabe 7 (TIA Portal, FUP)

Dieses Projekt zeigt die vollständige Umsetzung einer Sortieranlage in **Siemens TIA Portal** mit **FUP‑Programmierung**.  
Pakete werden erkannt, zeitverzögert transportiert und über drei Ausschieber gleichmäßig verteilt.  
Alle Netzwerke sind dokumentiert und als Screenshots beigefügt.

---

## 🚀 Funktionsübersicht

### ▶️ Start / Stop / Not‑Aus
- Start über **Taster_Start**
- Stop oder Not‑Aus schalten die Anlage sofort ab
- **Leuchte_Start** und **Leuchte_Stop** zeigen den Anlagenzustand an

### 🔄 Paketablauf
1. Paket wird am Einlauf erkannt  
2. Nach **1 Sekunde** Einschaltverzögerung startet das Förderband  
3. Paketverteilung über CTU‑Zähler:
   - 1. Paket → Ausschieber 1  
   - 2. Paket → Ausschieber 2  
   - 3. Paket → Ausschieber 3  
   - Danach wieder bei 1  
4. Jeder Ausschieber fährt aus, sobald sein Lichttaster belegt ist  
5. Nach dem Abtransport stoppt das Förderband automatisch  
6. Es liegt immer nur **ein Paket gleichzeitig** auf dem Band

---

# 🧩 Netzwerke im Detail

---

## 🟩 Netzwerk 2 – Start/Stop/Not‑Aus
![Netzwerk 2](Screenshots/Netzwerk2.PNG)

**Funktion:**  
SR‑Speicher für den Anlagenstart.  
Stop und Not‑Aus setzen die Anlage zurück.

---

## 🟩 Netzwerk 3 – Förderband mit TON
![Netzwerk 3](Screenshots/Netzwerk3.PNG)

**Funktion:**  
Der Einlauf-Lichttaster muss **1 Sekunde** belegt sein, bevor das Förderband startet.  
Merker „Förderband_belegt“ wird gesetzt.

---

## 🟩 Netzwerk 4 – Ausschieber 1 ansteuern
![Netzwerk 4](Screenshots/Netzwerk4.PNG)

**Funktion:**  
- Paket wird gezählt (CTU)  
- Wenn Zählerstand = 1 → Ausschieber 1 aktiv  
- Lichttaster löst Ausfahren aus

---

## 🟩 Netzwerk 5 – Ausschieber 2 ansteuern
![Netzwerk 5](Screenshots/Netzwerk5.PNG)

**Funktion:**  
- CTU zählt weiter  
- Wenn Zählerstand = 2 → Ausschieber 2 aktiv

---

## 🟩 Netzwerk 6 – Ausschieber 3 ansteuern
![Netzwerk 6](Screenshots/Netzwerk6.PNG)

**Funktion:**  
- CTU zählt weiter  
- Wenn Zählerstand = 3 → Ausschieber 3 aktiv  
- Danach Reset → Zyklus beginnt wieder bei 1

---

## 🟩 Netzwerk 7 – Leuchte Start
![Netzwerk 7](Screenshots/Netzwerk7.PNG)

**Funktion:**  
Leuchte_Start leuchtet, wenn Anlage läuft.

---

## 🟩 Netzwerk 8 – Leuchte Stop
![Netzwerk 8](Screenshots/Netzwerk8.PNG)

**Funktion:**  
Leuchte_Stop leuchtet, wenn Anlage gestoppt ist.

---

## 🟩 Netzwerk 9 – Motor Förderband
![Netzwerk 9](Screenshots/Netzwerk9.PNG)

**Funktion:**  
Förderband läuft nur, wenn:  
- Anlage gestartet  
- Förderband belegt

---

## 🟩 Netzwerk 10 – Ausschieber 1 ausfahren + Band
![Netzwerk 10](Screenshots/Netzwerk10.PNG)

**Funktion:**  
Ausschieber 1 fährt aus, wenn sein Lichttaster belegt ist.  
Band 1 läuft während des Ausschiebens.

---

## 🟩 Netzwerk 11 – Ausschieber 2 ausfahren + Band
![Netzwerk 11](Screenshots/Netzwerk11.PNG)

**Funktion:**  
Ausschieber 2 fährt aus, wenn sein Lichttaster belegt ist.  
Band 2 läuft während des Ausschiebens.

---

## 🟩 Netzwerk 12 – Ausschieber 3 ausfahren + Band
![Netzwerk 12](Screenshots/Netzwerk12.PNG)

**Funktion:**  
Ausschieber 3 fährt aus, wenn sein Lichttaster belegt ist.  
Band 3 läuft während des Ausschiebens.

---

# 🧠 Variablentabelle
![PLC Variablen](Screenshots/PLC_Variablen.PNG)

---

# 🎯 Ziel des Projekts
- Grundlagen der SPS‑Programmierung festigen  
- Arbeiten mit FUP, TON, CTU und SR  
- Realistische Sortierlogik umsetzen  
- Dokumentation für GitHub & Portfolio

---

# 📘 Hinweis
Dieses Projekt wurde bewusst in **FUP** umgesetzt.  
Eine spätere Erweiterung in **SCL** (State Machine) ist möglich.
