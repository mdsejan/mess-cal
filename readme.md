# 🧮 MealBook

> Simple Monthly Meal & Expense Manager for Boarding Houses

A lightweight web app to manage mess expenses, calculate meal rates, and generate reports. No installation required - works directly in your browser!

[![Live Demo](https://img.shields.io/badge/demo-live-success)](https://messcal.netlify.app/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Made with Love](https://img.shields.io/badge/Made%20with-❤️-red.svg)](https://messcal.netlify.app/)

---

## ✨ Features

- 📊 **Auto Calculations** - Meal rates, individual dues, and balances calculated automatically
- 👥 **Boarder Management** - Add, edit, and track boarders with deposits and meals
- 💰 **Expense Tracking** - Quick entry for market costs and extra expenses (Enter key support)
- 🖨️ **Dual Print Modes** - Summary overview or detailed boarder-wise report
- 💾 **Data Backup** - Export/import data as JSON files
- 📱 **Fully Responsive** - Works perfectly on mobile, tablet, and desktop
- 🎨 **Beautiful UI** - Modern gradient design with custom alerts
- ⌨️ **Keyboard Shortcuts** - Enter key support for quick data entry
- 🌐 **Offline Ready** - Uses LocalStorage, works without internet

---

## 🚀 Quick Start

### Option 1: Direct Download

```bash
# Clone the repository
git clone https://github.com/mdsejan/mess-cal.git

# Navigate to directory
cd mess-cal

# Open in browser
open index.html
```

## 📖 Usage Guide

### Getting Started

**1. Setup Mess Information**

> Enter mess name, manager name, and select the month

**2. Add Boarders**

> - Click "Add Boarder"
> - Enter name, deposit amount, and total meals consumed
> - Click "Add" button

**3. Track Bazar Costs**

> - Enter market/grocery expenses
> - Press Enter or click "Add" for quick entry

**4. Add Extra Expenses**

> - Enter utilities, gas, electricity, etc.
> - Press Enter or click "Add"

**5. View Summary**

> - Real-time calculation of meal rate
> - See total deposits, expenses, and dues
> - Check who needs to pay or get money back

**6. Generate Reports**

> - **Print Summary** - Quick overview with key metrics
> - **Print Full Report** - Detailed boarder-wise breakdown

---

### 💾 Data Management

<details>
<summary><b>Export Data (Backup)</b></summary>

1. Click **"💾 Export Data"** button
2. Save the JSON file to your device
3. File format: `mealbook-data-YYYY-MM-DD.json`

</details>

<details>
<summary><b>Import Data (Restore)</b></summary>

1. Click **"📤 Import Data"** button
2. Select your previously exported JSON file
3. Confirm to restore data

</details>

<details>
<summary><b>Clear All Data</b></summary>

1. Click **"🗑️ Clear All Data"**
2. Confirm deletion (⚠️ cannot be undone)

</details>

## 🧮 Calculation Logic

### 1️⃣ Meal Rate Calculation

> **Formula:**
>
> ```
> Meal Rate = Total Bazar Cost ÷ Total Meals
> ```

**📊 Example:**

| Item             | Value               |
| ---------------- | ------------------- |
| Total Bazar Cost | ৳15,000             |
| Total Meals      | 1,000               |
| **Meal Rate**    | **৳15.00 per meal** |

---

### 2️⃣ Individual Boarder Cost

> **Formulas:**
>
> ```
> Meal Cost = Number of Meals × Meal Rate
> Extra Cost Per Person = Total Extra Expenses ÷ Number of Boarders
> Total Cost = Meal Cost + Extra Cost Per Person
> ```

**📊 Example: Boarder A**

| Calculation Step | Value                     |
| ---------------- | ------------------------- |
| Number of Meals  | 80                        |
| Meal Rate        | ৳15.00                    |
| Meal Cost        | 80 × ৳15 = **৳1,200**     |
| Extra Cost       | ৳500 ÷ 10 = **৳50**       |
| **Total Cost**   | **৳1,200 + ৳50 = ৳1,250** |

---

### 3️⃣ Balance & Settlement

> **Formula:**
>
> ```
> Balance = Deposit - Total Cost
> ```

**💰 Settlement Rules:**

| Condition   | Meaning   | Action                                           |
| ----------- | --------- | ------------------------------------------------ |
| Balance > 0 | Overpaid  | ✅ Boarder will **GET** money back (refund)      |
| Balance < 0 | Underpaid | ⚠️ Boarder needs to **GIVE** money (payment due) |
| Balance = 0 | Exact     | ✔️ No settlement needed                          |

---

### 4️⃣ Manager Settlement

> **Formulas:**
>
> ```
> Manager Will Get = Sum of all GIVE amounts (money to collect)
> Manager Will Give = Sum of all GET amounts (money to return)
> Net Balance = Total Due = Total Used - Total Deposit
> ```

**📋 Summary:**

- **Manager Will Get:** Total amount to collect from boarders who underpaid
- **Manager Will Give:** Total amount to return to boarders who overpaid
- **Net Balance:** Overall surplus or deficit
