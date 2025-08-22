## Summary

This project demonstrates a lightweight JavaScript automation run directly in the browser DevTools console to recreate a HubSpot campaign after normalizing a spreadsheet of 750+ contacts. The workflow reduces several hours of repetitive work into a fraction of the time, showcasing browser scripting, DOM automation, and workflow optimization.

## Background / Problem

Manually re-adding 750+ contacts to a HubSpot campaign is time-consuming and prone to errors. The goal of this project was to automate the process, saving time while maintaining accuracy.

## Solution

I built a browser-based JavaScript automation by analyzing HubSpot’s HTML structure. The script performs the following:

- Imported and parsed CSV exports from HubSpot

- Automatically populated the search field with each contact’s name

- Paused for manual confirmation (checkbox selection)

- Resumed with the Enter key to continue processing the next contact

To identify the correct fields and buttons, I scraped the necessary selectors by inspecting the HubSpot page in the browser, ensuring the script interacted with the correct DOM elements.

This runs entirely in the DevTools console, requiring no additional setup.

## Results / Impact

- Reduced hours of manual campaign setup to minutes

- Minimized human error in repetitive tasks

- Demonstrated that automation doesn’t have to be complex to deliver meaningful efficiency improvements

## Lessons Learned / Key Takeaways

 - Inspecting the page to identify selectors is essential for browser-based automation

- Browser scripting and DOM manipulation can solve real-world workflow problems efficiently

- Simple, lightweight automation can dramatically improve efficiency

- Structuring scripts for pause and resume allows for a mix of automation and manual verification
