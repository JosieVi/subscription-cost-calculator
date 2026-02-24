# Subscription Pricing Calculator (QA Automation Tool)

An interactive tool for automated subscription cost calculation based on data from external Excel files.

## Key Features:

- **Client-Side Data Parsing:** Instant upload and processing of price lists (XLSX/XLS) directly in the browser.
- **Flexible Configuration:** Dynamic selection of tariff plans, regions, subscription terms, and client statuses.
- **Robust Error Handling:** Built-in validation for missing price matches, incorrect data formats, or empty files.
- **Optimized UI/UX:** Clean, responsive interface with instant results and a dedicated debug panel for data verification.

---

## Tech Stack:

- **HTML5 / CSS3** (Modern Flexbox layout)
- **JavaScript** (ES6+ logic and DOM manipulation)
- **[SheetJS](https://sheetjs.com/)** (Powerful library for Excel file parsing)

---

## How to Use

### Step 1: Prepare Your Price List File

Create an Excel file (.xlsx or .xls) with the following columns:

- **Plan Type** — Subscription plan name (e.g., Mobile, Basic, Standard, Premium, Corporate)
- **Region** — Geographic region (Finland, USA, Turkey, India)
- **Monthly Price** — Base monthly price as a number
- **Currency** — Currency code (e.g., EUR, USD, TRY, INR)

**Example:**
| Plan Type | Region | Monthly Price | Currency |
|-----------|--------|---------------|----------|
| Mobile | Finland | 9.99 | EUR |
| Basic | USA | 12.00 | USD |
| Premium | Turkey | 15.50 | TRY |

### Step 2: Automatic & Manual Price List Loading

The calculator automatically attempts to load a `test_price.xlsx` file from the server on startup.

- If the default file loads successfully, the **"Calculate Cost"** button will become active immediately.
- If the default file is not found or you wish to use a different price list:
  1. Click the **"Choose XLS, XLSX File"** button.
  2. Select your custom price list file (.xlsx or .xls).
  3. Wait for the confirmation message: "✅ File accepted. Rows loaded: X".
  4. The **"Calculate Cost"** button will become active.

### Step 3: Configure Calculation Parameters

Before calculating, select the following options:

- **Tariff Plan Type** — Choose from: Mobile, Basic, Standard, Premium, Corporate
- **Subscription Term (months)** — Enter 1–24 months
- **Usage Region** — Select: Finland, USA, Turkey, or India
- **Client Status** — Choose:
  - _New client_ — Receives 10% discount
  - _Repeat purchase_ — No discount applied
- **Extra Services** — Select:
  - _No Extra Slots_ — Standard pricing
  - _Add Extra Member Slot_ — Adds 10% to base cost

### Step 4: Calculate and Review Results

1. Click the **"Calculate Cost"** button
2. Results appear on the right side showing:
   - **Base Cost** — Price with extra services applied
   - **Discount** — Amount and percentage based on client status
   - **Total to Pay** — Price after discount
   - **Including Tax** — VAT amount and rate by region

### Step 5: Review Debug Information

At the bottom of the results panel, you'll find debug data showing:

- Selected plan type and region
- Monthly price and currency from the file
- Applied tax rate (VAT %)
- Discount rate (%)
- Extra service coefficient

**Debug data helps verify calculations are correct.**

### Error Handling

- **Missing Combination Error** — If the selected plan and region don't exist in the file, you'll see: "❌ Error: The combination was not found in the price list"
- **Invalid Price Error** — If a plan has an invalid or zero price, the calculator will display an error message
- **Empty File Error** — The system alerts if the uploaded file contains no data

### Fixed Rates & Discounts

The calculator uses predefined rates for VAT and discounts:

- **VAT Rates (Value Added Tax):**
  - Finland: 25.5%
  - USA: 0%
  - Turkey: 20%
  - India: 18%

- **Client Status Discounts:**
  - **New client:** 10% discount applied.
  - **Repeat purchase:** No discount applied.
