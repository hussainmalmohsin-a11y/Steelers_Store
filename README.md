# 🏈 SteelersStore (Java Swing)

A desktop **shopping & invoicing** demo built with Java and Swing. The app reads a product catalog from `items.txt`, lets customers select items and quantities via dialogs, calculates **tax** and **shipping**, and shows a formatted **invoice**.

---

## ✨ Features

- Loads items from a text file (`items.txt`), with code → name → price
- Guided purchase flow using Swing dialogs (`JOptionPane`)
- Calculates:
  - **Subtotal** (total before tax)
  - **Tax** at 7%
  - **Shipping**: $20 if subtotal < $100, otherwise free
- Pretty invoice using `JTextArea` (name, address, line items, totals)
- Basic validation and malformed line handling

---

## 🧱 Project Structure

```
steelers-store/
├─ src/
│  └─ SteelersStore/
│     └─ SteelerStore.java
├─ items.txt
├─ README.md
└─ .gitignore
```

## 🚀 Build & Run

### Prerequisites
- Java 11+ (Java 17 recommended)
- Terminal / Command Prompt

### Compile
```bash
# from project root
javac -d out src/SteelersStore/SteelerStore.java
```

### Run
```bash
java -cp out SteelersStore.SteelerStore
```

> Ensure `items.txt` is located in the **project root** (same directory you run from), or adjust the file path in `loadItems()`.

---

## 🧭 How to Use

1. On launch, the app:
   - Loads `items.txt`
   - Prompts for **name** and **address**
2. For each purchase:
   - Enter an **item code**
   - Enter a **quantity**
   - Confirm whether you want to **add more items**
3. When finished:
   - Totals are computed
   - A formatted **invoice** is displayed

### Invoice Example

```
Name: Troy Polamalu
Address: 43 Blitz Ave, Pittsburgh, PA

Items Purchased:
1003    Terrible Towel     $19.99  Quantity: 3   Total: $59.97
1005    Cap                $24.00  Quantity: 2   Total: $48.00

Total before tax: $107.97
Tax: $7.56
Shipping: $0.00
Final Amount Due: $115.53
```

---

## 🧮 Totals Logic

- **Subtotal**: sum of `price × quantity` across selected items
- **Tax**: `subtotal × 0.07`
- **Shipping**: `$20` if `subtotal < $100`, else `$0`
- **Final Amount**: `subtotal + tax + shipping`

---

## 🛡️ Error Handling

- **Malformed lines** in `items.txt` → warning dialog, line skipped
- **Unknown item codes** entered during purchase are ignored silently (could be enhanced—see roadmap)
- `NumberFormatException` while parsing shows an error dialog

---

## 🧰 Suggested `.gitignore`

```
# Build outputs
/out/
*.class

# IDE
.vscode/
.idea/
*.iml

# OS
.DS_Store
Thumbs.db
```

---

## 🗺️ Roadmap / Enhancements

- Validate entered **item codes** and show an error if not found
- Show a **catalog dialog** to pick items by name
- Persist purchases to CSV/JSON
- Configurable **tax** and **shipping** rules
- Discount codes, loyalty points
- Full GUI (table of items, add-to-cart, totals pane) with JavaFX or Swing
- Unit tests (JUnit) + CI (GitHub Actions)

## 📜 License

MIT – free to use for learning and portfolio projects.

