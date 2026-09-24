# Serial Date Reply Generator 🚀

A lightweight, high-performance web tool that calculates a dynamic reply from serial numbers based on standard date conversion and random day offset logic.

## 🌟 Live Demo & Preview
Open `index.html` directly in any web browser or run the local server.

---

## 📐 The Formula & Conversion Logic

The tool converts the first 4 characters of any serial number:

### 1. Extract First 4 Characters: `(Y, M, DD)`
* **Character 1 (`Y`):** Year offset from 2020
* **Character 2 (`M`):** Month representation
* **Characters 3 & 4 (`DD`):** Day of the month (01–31)

### 2. Convert to Standard Date
* $\text{Year} = 2020 + Y$
* $\text{Month} = \text{Decimal equivalent of } M$ ($1\dots9, \text{A}=10, \text{B}=11, \text{C}=12$)
* $\text{Day} = DD$

### 3. Add Random Days
* Randomly picks: **$+2$**, **$+3$**, or **$+4$** days.
* Adds the days to the standard date using UTC date arithmetic (accurately handles month rollovers, leap years, and year-end transitions).

### 4. Convert Back to 4-Digit Reply Format
* **1st Digit:** Last digit of the calculated new year ($2024 \to 4$, $2025 \to 5$)
* **2nd Digit:** Hexadecimal equivalent of the new month ($1\dots9, \text{A}, \text{B}, \text{C}$)
* **3rd & 4th Digits:** New 2-digit day ($01\dots31$)

---

## 🧪 Examples

| Input Serial | Prefix | Original Date | Days Added | New Date | Reply 4-Digit | Full Updated Serial |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `4C15` | `4C15` | 2024-12-15 | +3 days | 2024-12-18 | `4C18` | `4C18` |
| `4C15ABC123` | `4C15` | 2024-12-15 | +3 days | 2024-12-18 | `4C18` | `4C18ABC123` |
| `4929` | `4929` | 2024-09-29 | +3 days | 2024-10-02 | `4A02` | `4A02` |
| `4C30` | `4C30` | 2024-12-30 | +3 days | 2025-01-02 | `5102` | `5102` |
| `4228` (Leap) | `4228` | 2024-02-28 | +2 days | 2024-03-01 | `4301` | `4301` |

---

## 🛠️ Features
- **Zero Dependencies:** Pure standalone HTML, CSS, and vanilla JavaScript.
- **Instant Live Calculation:** Updates dynamically as you type.
- **1-Click Copy:** Instant clipboard copy for single reply or full updated serial.
- **Roll Again (🎲):** Quickly re-rolls random offsets (+2, +3, or +4) or select a fixed offset.
- **Formula Breakdown Card:** Transparent, real-time explanation showing every step.
- **Batch Processing:** Paste a multi-line list of serial numbers to compute all at once, with 1-click bulk copy or CSV export.

---

## 💻 Local Testing
Simply open `index.html` in any browser, or run:
```bash
python -m http.server 8089
```
Then visit `http://localhost:8089`.

---

## 📄 License
MIT License.
