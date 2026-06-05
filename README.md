# CSARCH2 Virtual Exhibit Proposal

**Group Name:** Project Y2K  
**Topic Theme:** The Y2K Bug in the 20th Century

## Group Members

- Adrian Matthew Dee
- Alain Zuriel Marcos
- Elkan La Madrid
- Jenrick Lim
- Kent Lopez

---

## Tech Stack

### Frontend

| Technology | Role |
|---|---|
| Astro 6 | Primary framework; required by the project template; handles museum page rendering |
| React (JSX) | All interactive exhibit elements — simulations and educational games as reusable JSX components embedded via MDX |
| MDX | Main exhibit content page; combines written content with embedded React components |
| CSS | Styling; used to replicate the visual aesthetic of late-1990s computing environments |

### Backend

| Technology | Role |
|---|---|
| Node.js | Runtime environment for local development and Astro deployment |
| Express | Included as a contingency for additional backend functionality if needed |

---

## I. Proposed Structure

### 1. Introduction (Story Hook)

- What is Y2K?
- Why everyone feared the year 2000
- "Would computers think 2000 = 1900?"

### 2. Technical Explanation (CSARCH Core)

#### a. 2-Digit Year Storage

In the early years of computing, storage was extremely expensive. Programmers stored years as only 2 digits to conserve space. COBOL, the dominant language of the era, reflected this in its data definitions via 6-digit date fields: `PIC 9(6)`.

#### b. Memory Limitations

The problem existed at the hardware level as well — not just in code. BIOS chips and Real-Time Clock (RTC) chips stored dates in a 2-digit BCD (Binary Coded Decimal) format.

#### c. Ambiguity

Since `"00"` was ambiguous, machines encountered problems because there was no proper definition for the year 2000.

```
1999 → "99"
2000 → "00"  ← interpreted as 1900
```

This caused three main failure modes:

1. **Negative arithmetic** — e.g., a person born in 1950 would be calculated as -50 years old
2. **Wrong sort order** — data from 2000 onwards would appear *before* 1999 data (`"99" > "00"`)
3. **Crashes** — some systems rejected `"00"` as invalid input entirely

### 3. Timeline (Visual Section)

| Period | Event |
|---|---|
| 1970–1990 | Systems designed with 2-digit year shortcuts |
| 1995–1999 | Public and industry panic begins |
| 1999–2000 | Global remediation effort underway |

---

## II. Interactive Components

### 1. Simulation — "The Year Counter: Stop at 2000"

**Concept:** A system clock simulation counting years from 1990 → 2000.

**Gameplay:**
- The counter ticks forward: 1990, 1991, 1992 … 1998, 1999, 2000
- The user can press a button at any time to pause it
- If the counter reaches 2000 → crash animation plays, then resumes after any button press
- After the crash, it loops back to 1990 and repeats

**What it teaches:**
- The rollover bug threat
- Integer overflow and misinterpretation
- System failure as a consequence of data representation

---

### 2. Game — "Midnight Crisis Fix-it"

**Concept:** You are a software engineer on December 31, 1999. Fix the systems before midnight.

**Gameplay:**
- Choose from a list of systems to patch, each costing "time":
  - `[1]` Banking System
  - `[2]` Airline Reservation System
  - `[3]` Hospital Records
  - `[4]` Power Grid
- A 12-minute real-time timer runs, displayed as 24 hours (2× speed): `23:58 → 23:59 → 00:00`

**Outcome states:**
- All systems fixed → **World is Stable** ending
- Systems missed → **System Collapse Simulation**

**What it teaches:**
- Prioritization in system design
- Real-world engineering constraints
- Why the Y2K remediation effort cost billions

---

## III. Proposed Design Layout

### PC Display

*(Mockup to be added)*

### Mobile Display

*(Mockup to be added)*
