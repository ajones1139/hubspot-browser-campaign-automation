# HubSpot Campaign Automation Case Study

## Summary
This project demonstrates a **lightweight JavaScript automation** run directly in the **browser DevTools console** to recreate a HubSpot campaign after normalizing a spreadsheet of 750+ contacts. The workflow reduces several hours of repetitive work into a fraction of the time, showcasing browser scripting, DOM automation, and workflow optimization.

## Background / Problem
Manually re-adding 750+ contacts to a HubSpot campaign is time-consuming and prone to errors. The goal of this project was to **automate the process**, saving time while maintaining accuracy.

## Solution
I built a **browser-based JavaScript automation** by analyzing HubSpot’s HTML structure. The script performs the following:

- **Import and parse CSV exports** from HubSpot
- **Automatically populate** the search field with each contact’s name
- **Pause for manual confirmation** (checkbox selection)
- **Resume with the Enter key** to continue processing the next contact

To identify the correct fields and buttons, I **scraped the necessary selectors by inspecting the HubSpot page**, ensuring the script interacted with the correct DOM elements. This runs entirely in the **DevTools console**, requiring no additional setup.

---

## Technical Approach
The automation script is designed to:

1. **Parse the CSV** and extract first and last names
2. **Type names slowly** into the HubSpot search field to simulate manual input
3. **Pause for verification** before continuing to the next contact
4. Repeat until all contacts are processed

### Code Excerpts

**React-safe input typing:**
```javascript
function setReactValue(el, value) {
  const last = el.value;
  el.value = value;
  const tracker = el._valueTracker;
  if (tracker) tracker.setValue(last);
  el.dispatchEvent(new Event("input", { bubbles: true }));
}

async function typeSlow(el, text, delay = 100) {
  el.focus();
  el.select?.();
  setReactValue(el, "");
  for (const ch of text) {
    setReactValue(el, (el.value || "") + ch);
    await new Promise(r => setTimeout(r, delay));
  }
}
```
## Waiting for manual confirmation:
```javascript
console.log("Check it manually, then press Enter to move on...");
await new Promise(resolve => {
  const handler = (e) => {
    if (e.key === "Enter") {
      window.removeEventListener("keydown", handler, true);
      resolve();
    }
  };
  window.addEventListener("keydown", handler, true);
});
```
These snippets show how the script safely interacts with React-controlled inputs and combines automation with manual verification.

## Results / Impact

- Reduced hours of manual campaign setup to minutes

- Minimized human error in repetitive tasks

- Demonstrated that automation doesn’t have to be complex to deliver meaningful efficiency improvements

## Lessons Learned / Key Takeaways

- Inspecting the page to identify selectors is critical for browser automation

- Simple JavaScript and DOM manipulation can solve real-world workflow problems efficiently

- Structuring scripts to pause and resume allows for safe human verification

## Demo
![Automation Demo][demo]

[demo]: hubspot-browser-campaign/demo.gif

