# 🏦 NOWA Bank — Banking Account Simulator

A professional, web-based banking simulator built with **Python** and **Gradio**. NOWA Bank lets users sign in, deposit and withdraw money, switch between **USD** and **Bahraini Dinar (BHD)**, and view a filterable mini statement, all in a clean, branded interface.

> ⚠️ **Educational project.** No real money or real banking data is involved. Accounts are simulated and reset every session.

---

## ✨ Features

- **Secure-style login** with a user ID and password, plus a logout page and a "Return to Login" flow
- **Deposit & Withdraw** with full validation (positive numbers only, insufficient-funds checks)
- **Dual currency support**: toggle between USD and BHD with one click
  - Fixed peg: `1 USD = 0.378 BHD`
  - USD is shown with **2 decimals**, BHD with **3 decimals**
- **Safe amount handling**: values are *truncated, never rounded up* (e.g. `12.9999` → `12.99`), so the customer is never credited more than they typed
- **Check Balance** in the selected currency
- **Mini Statement** with filters:
  - By transaction type (All / Deposit / Withdraw)
  - By date (All Dates / Custom Range, `YYYY-MM-DD`)
- **Reset Account** to the starting balance of $500
- **Custom branded UI**: custom theme, CSS, logo, and dashboard layout
- **Robust error handling** on every banking action

---

## 🧠 How It Works

| Concept | Details |
|---|---|
| Internal storage | All balances and transactions are stored in **USD**, so switching currency never changes the real account value |
| Precision | `Decimal` with `ROUND_DOWN` is used to avoid floating-point rounding surprises |
| Session state | Balance, transaction ledger, and currency are kept in Gradio `State` objects |
| Starting balance | New sessions start with a **$500.00** deposit |
| Input validation | Rejects empty, negative, zero, non-numeric, `NaN`, and `inf` values on the server side (the `+` / `-` keys are also blocked in the browser) |

---

## 🛠️ Tech Stack

- **Python 3.10+**
- **[Gradio](https://www.gradio.app/)**: UI framework
- Standard library: `datetime`, `decimal`

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
```

### 2. Install dependencies

```bash
pip install gradio jupyter
```

### 3. Run the project

Open the notebook and run all cells:

```bash
jupyter notebook NOWA_Bank_Project_1.ipynb
```

The app will start locally at:

```
http://127.0.0.1:7860
```

> To get a temporary public link, change `app.launch(...)` to `app.launch(share=True, ...)`.

---

## 🔑 Demo Login

The project includes a few **demo-only** accounts defined in the `USERS` dictionary inside the notebook. Open the notebook to see them, or add your own.

> 🔒 In a real application you should never hard-code credentials. Use hashed passwords and a proper authentication system.

---

## 📖 Usage

1. **Sign in** with a demo account.
2. Enter an **amount** and press **Deposit** or **Withdraw**.
3. Press the **Currency** button to switch between USD and BHD.
4. Use **Check Balance** to see your current balance.
5. Use **Mini Statement** to see your transactions, and filter them by type or date.
6. Press **Reset Account** to start over, or **Exit** to log out.

---

## 📁 Project Structure

```
.
├── NOWA_Bank_Project_1.ipynb   # Main notebook (logic + Gradio UI)
└── README.md
```

---

## 🔮 Future Improvements

- Persistent storage with a database (SQLite / PostgreSQL)
- Hashed passwords and real authentication
- Transfers between accounts
- Support for more currencies with live exchange rates
- Export statements to PDF / CSV
- Unit tests for the banking functions

---

## 👤 Author

**Noor**

Feel free to ⭐ the repo if you like it!

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
