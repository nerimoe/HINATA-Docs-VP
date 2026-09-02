# Write to Card

HINATA Go supports writing **Aime** or **Banapass** Access Codes to blank cards, allowing them to be used directly as game cards on supported arcade machines.

::: tip Use Cases
* Writing an Access Code to the blank card included with the HINATA Standard Edition.
* Writing an Access Code to compatible cards purchased separately.
* If you are using original cards (e.g. Amusement IC, original Aime/BANA cards), no writing is needed; you can use them directly.
:::

---

## Hardware and Card Requirements

### 1. Supported Target Cards
* **MIFARE Classic 1K cards (4-byte UID)**.
* Must be unencrypted blank cards or cards with default/known sector keys.

::: warning ⚠️ Unsupported Cards
* **Amusement IC cards**: Use secure chips (FeliCa, MIFARE Plus/DESFire) and cannot be written to.
* **Transit cards / Mobile NFC emulation**: Cannot be written to.
* **Non-4-byte UID or non-1K cards**: The app will report an unsupported target card type.
:::

### 2. Supported Devices and Platforms
Card writing requires NFC hardware provided via either:
* **Android Phone**: Using the device's built-in NFC sensor.
* **External HINATA / HINATA Lite Card Reader**: Connected via USB / WebHID (supported in web browser at `go.neri.moe`, Android app, etc.).

---

## Write Modes

When writing, HINATA Go provides two access control modes:

| Mode | Characteristics | Description |
| :--- | :--- | :--- |
| **Rewritable** | Flexible & Editable | Retains write permissions after data is written. You can update or rewrite the card later if needed. **(Recommended)** |
| **Permanently Read-Only** | Tamper-proof & Irreversible | Locks sector access bits to permanently read-only. Once locked, **no tool can rewrite or revert the card**. A confirmation dialog is required. |

::: note
Regardless of the write mode chosen, writing **does not alter the card's original physical UID** (it only writes the game sector data blocks).
:::

---

## Step-by-Step Instructions

### Step 1: Prepare the Access Code

Writing requires a valid 20-digit Access Code (usually a **20-digit number not starting with 3**). You can prepare this card in HINATA Go in any of the following ways:

1. **Saved Cards**: If the card is already saved in Favorites or a folder, proceed directly to the next step.
2. **Scan History**: If you have scanned the card before, locate it from scan history.
3. **Add Manually**: Go to the **Cards** page, tap **Add Card** in the bottom right corner, enter a custom name and the 20-digit Access Code, then save.

### Step 2: Open Card Details and Tap Write

1. Tap the target card in the list to open its details page.
2. In the bottom action bar, tap the **Write** button (with an NFC icon).

### Step 3: Select Write Mode and Start

1. In the "Write MIFARE Card" dialog, select the write mode (**Rewritable** or **Permanently Read-Only**).
2. Tap **Start Write**.
   * If you selected "Permanently Read-Only", confirm the warning prompt to proceed.

### Step 4: Present Card to Writer

1. The screen will prompt: "Please hold a MIFARE Classic 1K card near your phone or card reader".
2. Hold the blank card against your phone's NFC antenna area, or place it on your connected HINATA reader.
3. The app will automatically perform:
   * Checking card type
   * Checking sector keys and permissions
   * Writing card data
   * (If locking, writing access bits)
   * Verifying written data
4. When the interface displays **Card written and verified successfully**, tap **Done** and remove the card.

---

## Troubleshooting

* **"Card writing requires Android NFC or a connected HINATA card reader"**:  
  Ensure an NFC source is available. On PC/Web, connect and authorize your HINATA reader first. On mobile, ensure NFC is enabled in system settings.
* **"Please use a MIFARE Classic 1K card with a 4-byte UID"**:  
  The card placed is not a standard MIFARE Classic 1K (e.g. transit cards, Amusement IC, or 7-byte UID cards).
* **"Unable to authenticate card with supported keys"**:  
  The card sectors are protected with custom unknown keys and cannot be written as a blank card.
* **"Card was removed or timed out waiting for card"**:  
  The card moved or was taken away prematurely during writing. Tap Start Write again and hold the card firmly until finished.
