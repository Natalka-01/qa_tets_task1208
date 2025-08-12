# qa_tets_task1208

qa_tets_task1208

## Task 01

## Test Suite 00001 — FreeRule (Buy N, Get N Free)

---

### TC01 Add a single unit to the cart (no discount expected)

**Purpose:**  
Verify basic add-to-cart functionality and confirm that FreeRule does not apply when the threshold is not met.

**Preconditions:**

- User is signed in.
- Cart is empty.
- Environment URL: `http://localhost:3000`
- FreeRule feature is enebled

**Test Data:**

- Item: Green Tea (GR1)
- Unit price: £3.11

**Steps:**

1. Navigate to the website.
2. Add 1 unit of GR1 to the shopping cart.

**Expected Results:**

- Cart displays GR1 × 1 with unit price £3.11.
- No discount/free item is shown.
- Cart total = £3.11.

**Actual Result:**  
_Status:_ (Pass/Fail)

---

### TC02 — Apply FreeRule for 2 units

**Purpose:**  
Verify that 2 units charge only 1 unit’s price.

**Preconditions:**  
Same as TC01.

**Test Data:**

- Item: GR1
- Unit price: £3.11

**Steps:**

1. Navigate to the website.
2. Add 2 units of GR1.

**Expected Results:**

- Cart shows GR1 × 2.
- 1 free item applied.
- Cart total = £3.11.

**Actual Result:**  
_Status:_ (Pass/Fail)

---

### TC03 — Verification of three the same units in the cart.

**Purpose:**  
Verify correct charging when one pair is free and one extra unit is paid.

**Preconditions:**  
Same as TC01.

**Test Data:**

- Item: GR1
- Unit price: £3.11

**Steps:**

1. Navigate to the website.
2. Add 3 units of GR1.

**Expected Results:**

- Cart shows GR1 × 3.
- 1 free item applied.
- Charged units: 2.
- Cart total = £6.22.

**Actual Result:**  
_Status:_ (Pass/Fail)

---

### TC04 — Attempt to exceed maximum quantity

**Purpose:**  
Verify the system blocks quantities above the allowed maximum.

**Preconditions:**

- User is signed in.
- Cart is empty.
- FreeRule for GR1 is active.
- Max 10 units per order.

**Test Data:**

- Item: GR1
- Unit price: £3.11

**Steps:**

1. Navigate to the website.
2. Attempt to add 11 units of GR1 (or set quantity to 11 from the cart).

**Expected Results:**

- A validation error is shown: "Maximum quantity per order is 10 units".
- Quantity remains capped at 10 units.
- For 10 units:
  - Free items: 5.
  - Charged units: 5.
  - Cart total = **£15.55**.

**Actual Result:**  
_Status:_ (Pass/Fail)

## Test Suite 00003 ReducedPriceRule (Buy more than N, pay a different price)

---

### TC01 — Buy exactly N units (no discount)

**Purpose:**  
Verify that the discount does not apply when buying exactly the threshold quantity.

**Preconditions:**

- User signed in, cart empty.
- ReducedPriceRule configured for SR1 in data base

**Test Data:**

- Item: Strawberries (SR1)
- Original unit price: £5.00

**Steps:**

1. Navigate to the website.
2. Add 3 units of SR1 to the cart.

**Expected Results:**

- Cart shows SR1 × 3 at £5.00 each.
- No discount applied.
- Cart total = £15.00.

**Actual Result:**  
_Status:_ (Pass/Fail)

---

### TC02 — Buy more than N units (discount for all units)

**Purpose:**  
Verify that when the threshold is exceeded, all units are priced at the reduced price.

**Preconditions:** Same as TC01.

**Test Data:**

- Item: SR1
- Original unit price: £5.00

**Steps:**

1. Navigate to the website.
2. Add 4 units of SR1 to the cart.

**Expected Results:**

- Cart shows SR1 × 4 at £4.50 each.
- Discount applied to all 4 units.
- Cart total = £18.00.

**Actual Result:**  
_Status:_ (Pass/Fail)

---

### TC03 — Buy maximum allowed units (discount applied)

**Purpose:**  
Verify that the discount applies correctly when buying the maximum allowed quantity.

**Preconditions:** Same as TC01.

**Test Data:**

- Item: SR1
- Original unit price: £5.00

**Steps:**

1. Navigate to the website.
2. Add 10 units of SR1 to the cart.

**Expected Results:**

- Cart shows SR1 × 10 at £4.50 each.
- Discount applied to all 10 units.
- Cart total = £45.00.

**Actual Result:**  
_Status:_ (Pass/Fail)

---

### TC04 — Attempt to exceed maximum quantity

**Purpose:**  
Verify the system blocks quantities above the allowed maximum.

**Preconditions:** Same as TC01.

**Test Data:**

- Item: SR1
- Original unit price: £5.00
- Reduced unit price (if qty > 3): £4.50

**Steps:**

1. Navigate to the website.
2. Attempt to add 11 units of SR1 to the cart.

**Expected Results:**

- A validation error is shown: "Maximum quantity per order is 10 units."
- Quantity remains capped at 10 units.
- Unit price = £4.50 for all 10 units.
- Cart total = £45.00.

**Actual Result:**  
_Status:_ (Pass/Fail)

## Test Suite 00003 — FractionPriceRule (Buy more than N, pay a percentage of the original price)

---

**TC01 — Buy exactly N units (no discount)**  
**Purpose:** Verify that the percentage discount does not apply when purchasing exactly the threshold quantity.  
**Preconditions:**

- User signed in, cart empty.
- FractionPriceRule configured for CF1.

**Test Data:** CF1, £11.23

**Steps:**

1. Navigate to the website.
2. Add 2 units of CF1 to the cart.

**Expected Results:**

- Cart shows CF1 × 2 at £11.23 each.
- No discount applied.
- Cart total = £22.46.

**Actual Result:**  
_Status:_ (Pass/Fail)

---

**TC02 — Buy more than N units (discount for all units)**  
**Purpose:** Verify that once the threshold is exceeded, all units are priced at the discounted percentage.  
**Preconditions:** Same as TC01.

**Test Data:** CF1, £11.23; discounted unit price = £7.49 if quantity > 2.

**Steps:**

1. Navigate to the website.
2. Add 3 units of CF1 to the cart.

**Expected Results:**

- Cart shows CF1 × 3 at £7.49 each.
- Discount applied to all 3 units.
- Cart total = £22.47.

**Actual Result:**  
_Status:_ (Pass/Fail)

---

**TC03 — Buy maximum allowed units (discount applied)**  
**Purpose:** Verify discount and total at the maximum permitted quantity.  
**Preconditions:** Same as TC01, max 10 units per order.

**Test Data:** CF1, £11.23; discounted unit price = £7.49 if quantity > 2.

**Steps:**

1. Navigate to the website.
2. Add 10 units of CF1 to the cart.

**Expected Results:**

- Cart shows CF1 × 10 at £7.49 each.
- Discount applied to all 10 units.
- Cart total = £74.90.

**Actual Result:**  
_Status:_ (Pass/Fail)
