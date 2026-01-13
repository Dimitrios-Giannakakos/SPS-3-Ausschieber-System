# 📦 Sortieranlage mit Förderband & 3 Ausschiebern  
### (TIA Portal, FUP)

Dieses Projekt zeigt die Umsetzung einer Sortieranlage in **Siemens TIA Portal** mit **FUP‑Programmierung**.  
Pakete werden erkannt, zeitverzögert transportiert und über drei Ausschieber gleichmäßig verteilt.

---

## 🚀 Funktionsübersicht

### ▶️ Start / Stop / Not‑Aus
- Anlage startet über **Taster_Start**  
- Stop oder Not‑Aus schalten die Anlage sofort ab  
- **Leuchte_Start** und **Leuchte_Stop** zeigen den Anlagenzustand an

### 🔄 Paketablauf
1. Paket wird am Einlauf über Lichttaster erkannt  
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

## ⚙️ Technische Umsetzung

- **FUP‑Netzwerke** für Start/Stop, Förderband, Ausschieber 1–3  
- **TON‑Timer** für Einschaltverzögerung  
- **CTU‑Zähler** für die Paketverteilung  
- **SR‑Logik** für Ausschiebersteuerung  
- **Meldeleuchten** für Betriebszustände  
- **Screenshots aller Netzwerke** im Ordner `/screenshots`

---

## 🧠 Operanden (Auszug)

**Eingänge:**  
- %E0.0 Taster_Start  
- %E0.1 Taster_Stop  
- %E0.2 NotAus  
- %E0.3–E0.6 Lichttaster Einlauf & Ausschieber  

**Ausgänge:**  
- %A0.0 Leuchte_Start  
- %A0.1 Leuchte_Stop  
- %A0.2 Motor_Förderband  
- %A0.3–A1.0 Ausschieber 1–3 + Bänder  

**Merker:**  
- Förderband_belegt  
- Ausschieber1/2/3_ansteuern  
- Zählerstände (CTU)

---

## 📸 Screenshots
Alle Netzwerke befinden sich im Ordner **/screenshots**:
- Start/Stop  
- Förderband  
- Ausschieber 1–3  
- Meldeleuchten  
- Motorsteuerung  
- Variablentabelle  

---

## 🎯 Ziel des Projekts
- Grundlagen der SPS‑Programmierung festigen  
- Arbeiten mit FUP, TON, CTU und SR  
- Realistische Sortierlogik umsetzen  
- Dokumentation für GitHub & Portfolio

---

## 📘 Hinweis
Dieses Projekt wurde bewusst in **FUP** umgesetzt.  
Eine spätere Erweiterung in **SCL** (State Machine) ist möglich.
