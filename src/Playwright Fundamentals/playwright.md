# Playwright

- [Playwright](www.playwright.com) is a Node.js library to automate Chromium, Firefox and WebKit with a single API. It is built to enable cross-browser web automation that is ever-green, capable, reliable and fast.
<sub>Reference [Playwright](www.playwright.com)</sub>

# Getting Started
Install Playwright
````bash
npm init playwright@latest
````

Update latest version of Playwright Test
````bash
npm init -D playwright/test@latest
````
- Main Concepts
  - Browser: A browser instance (Chromium, Firefox, WebKit)
  - Context: An isolated incognito-like session within a browser
  - Page: A single tab or window within a context
  - Locator: A way to find elements on a page
  - POM: Page Object Model, a design pattern for creating reusable and maintainable test code

## Interaction with Web Elements

### Locating Elements

### Extracting Values

### Fixtures
````javascript
export const test = base.extend({
    // Define fixture setup and teardown logic here
    pageManager: [async ({ page }, use) => {
        const pm = new PageManager(page)
        await use(pm);
        console.log('Teardown logic After execute  pageManager fixture');
    }, auto: true}] - run automatically even beforeeach and beforeall
})
````
> Sequence of execution on Fixtures
```javascript
export const test = base.extend({
    fixture01: async ({ page }, use) => {
               const pm = new PageManager(page)   // Executed step 1
               await use('');
               console.log('Teardown logic After test was completed'); // Executed step 5
    }
,
    fixture02: async ({ page, fixture01 }, use) => {
               const a = new A (page)  // Executed step 2
               await use(a);
               console.log('Teardown logic After execute the test under fixture02'); // Executed step 4
    }
})
     test.spec.js file
     test('Test case', async ({ fixture02 }) => {)
         console.log('Test case execution');  // Executed step 3
     })


```

### Assertions
> [!NOTE] Playwright has 2 types of assertions: General Assertions and Locator Assertions
```javascript
// General Assertions compare value to the left with value to the right
expect(value).toBe(expected);
expect(value).toEqual(expected);
expect(value).toContain(expected);
expect(value).toMatch(expected);
````
````javascript
// Locator Assertions
await expect(locator).toBeVisible();
await expect(locator).toBeEnabled();
await expect(locator).toHaveText(expected);
await expect(locator).toHaveAttribute(name, value);
await expect(locator).toHaveCSS(property, value);
````

### Screenshots
```` javascript
 await page.screenshot({ fullPage: true, path: 'screenshots/worker-settings.png' });
 await page.locator('locatorToCapture').screenshot()
````
````javascript
 const buffer = await page.screenshot()
 console.log(buffer.toSring('base64')) -
````

### Auto-Waiting
> [!IMPORTANT]
> Playwright performs auto-waiting for elements to be ready before performing actions on them.
> Attached, Visible, Stable, Enabled, Editable, Hidden, Detached



### Timeouts
````javascript
globalTimeout: 160_000,  //Limit of the whole test suite
testTimeout: 30_000,     //Limit of each test
actionTimeout: 5_000,    //Limit of each action (click, fill, etc.)
navigationTimeout: 30_000, //Limit of each navigation (goto, waitForNavigation, etc.)
defaultTimeout: 5_000,   //Default limit for all the above timeouts (except globalTimeout)
setDefaultTimeout(timeout), //Set default timeout for all the above timeouts (except globalTimeout)
expect: { timeout: 160_000 },    //Time Limit for expect locator assertions (expect)
````



####
> [!IMPORTANT]
> Playwright by default run test in parallel assigning 1 independent worker per spec file

# Parallel and Serial Execution
```javascript
test.describe.configure({ mode: 'parallel' }); // Run tests in parallel (default)
test.describe.configure({ mode: 'serial' });   // Run tests in serial (one after another)
````



> [!IMPORTANT]
> Desestructurar en JavaScript
````javascript
  const {status, body} = response; - Desestructuración para extraer el status y el body de la respuesta.
  const {status, body: { data: { meta: { message } } }} = response; - Desestructuración anidada para extraer el mensaje del meta dentro del data del body de la respuesta.
  const { status, body: {data, data: { meta: { message } } } } = response;

````

````javascript
if (![200, 201].includes(status))  - Verifica si el status de la respuesta no es 200 o 201, lo que indica un error en la solicitud.

````

> [!IMPORTANT]
> List and Dropdown
```javascript
await page.getByRole('list')        //When the List has a UL tag
await page.getByRole('listitem');   //When the List has a LI tag
````