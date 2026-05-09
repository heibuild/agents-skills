---
name: playwright-screenshot
description: Take screenshots of a website using the Playwright CLI. Use when the user wants to verify UI, check page layout, or get visual feedback on a specific page. Screenshots are saved to ./screenshots/ in the project root.
---

# Playwright CLI Screenshot Skill

Use this skill to take screenshots of a website for visual feedback.

## Usage

1. Ask the user or infer the website to check from the context
2. Ensure the website is running and accessible
3. Determine the URL path based on context (e.g. `/hamburg/flohschanze`, `/`, `/hamburg/isemarkt`)
4. Create the screenshots directory if it doesn't exist (`mkdir -p ./screenshots`
5. Ask the user if there is a cookie consent banner that needs to be bypassed, and if so, ensure the appropriate cookies are stored in `playwright/cookies.json` - see command to open up a browser for manual cookie capture below
6. Run the Playwright screenshot command either for web or mobile, with or without cookies, depending on the context and user input

npx playwright screenshot --device "iPhone 15" --load-storage=playwright/cookies.json http://localhost:4321 ./screenshot.png

## Commands

### Normal Web Screenshot

```
npx playwright screenshot <url>/<path> ./screenshots/<name>.png
```

### Web Screenshot with Cookies

```
npx playwright screenshot --load-storage=playwright/cookies.json <url>/<path> ./screenshots/<name>.png
```

### iPhone / Mobile Screenshot with Cookies

```
npx playwright screenshot --device "iPhone 15" --load-storage=playwright/cookies.json <url>/<path> ./screenshots/<name>.png
```

### Open Playwright Browser for Manual Cookie Capture

```
npx playwright open --save-storage=playwright/cookies.json <url>
```

## Example

```bash
mkdir -p ./screenshots
npx playwright screenshot --load-storage=playwright/cookies.json <url>/<path> ./screenshots/<name>.png
```

After taking the screenshot, read the file with the Read tool to display it visually for feedback.
