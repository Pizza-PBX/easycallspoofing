# FreePBX Caller ID Spoofing Setup (Works for FreePBX 15 and 16)

**It may work with FreePBX 17 as well**, but you will not be able to change the Context (they removed the option).  
In that case, you will have to change `CUSTOM_STUFF` to `from-internal` in the code.

### Why This Matters
With the custom context option you can have **both** a `CUSTOM_STUFF` and a `from-internal` context.  
This allows you to have **2 different extensions**:
- One where you can spoof a custom number manually (using the `from-internal` one)
- One where you can auto-spoof using the dial patterns (using the `CUSTOM_STUFF` one)

### Setup Steps

1. In your FreePBX dashboard go to **Admin > Config Edit** (or directly to `extensions_custom.conf`).
2. Paste the code provided in the GitHub into `extensions_custom.conf` (click **Save** and **Apply Config**).
3. Create your extensions in **Connectivity > Extensions**:
   - One **normal extension** – change nothing.
   - One **spoofing extension** – go to the **Advanced** tab and change the **Context** to `CUSTOM_STUFF`.  
     (Save and Apply Config)

**Important Note on the Code:**  
In the code, look at the **second-to-last line** for each number pattern where it says `BulkVS,30`.  
**Change `BulkVS`** to the **exact name of your SIP Trunk** in FreePBX and leave the `,30` unchanged.

### How It Works (on the CUSTOM_STUFF extension)

- `XXX-XXX-XXXX` = Uses **Custom Caller ID** that you set through the extension (works on `from-internal` only)  
- `2*XXX-XXX-XXXX` = Spoofs Caller ID to **mimic the area code** and randomly generates the remaining numbers  
- `3*XXX-XXX-XXXX` = Spoofs Caller ID to a **random 1800 number**  
- `4*XXX-XXX-XXXX` = Spoofs Caller ID to **mimic the number you are dialing**  
- `5*XXX-XXX-XXXX` = Spoofs Caller ID to a **completely randomly generated number**  
- `6*XXX-XXX-XXXX` = Spoofs Caller ID to mimic the dialed number **except the last digit**, which is randomized

**Tip:** Use the normal extension for regular calls and the spoofing extension (with `CUSTOM_STUFF` context) when you want to use the special `*` patterns. 
