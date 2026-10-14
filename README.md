# UdyamMitra — responsive rural business toolkit

A mobile- and desktop-friendly prototype for entrepreneurs in Maharashtra. The interface can be switched between English and Marathi.

## Features

- Local prototype registration and login.
- English / Marathi language switch.
- Production quantity and cost-based pricing calculator.
- Government of India data.gov.in / AGMARKNET mandi price connector.
- Clear status messages when live data is unavailable; the app does not substitute sample values for failed live requests.
- Local price book with CSV export.
- Inventory tracking, low-stock warnings, sale records, estimated gross profit and downloadable simple receipts.
- Customer order tracking; fulfilling an order updates stock and records a sale.
- Buyer / shop / SHG contact directory with CSV export.
- Distribution channel cost comparisons.
- Business learning tips, official IMD weather link and browser voice navigation where supported.
- Basic offline cache when hosted over HTTPS or localhost.

## Run the app

1. Extract the ZIP file.
2. Open `index.html` in a current desktop or mobile browser.
3. To test offline caching / installability, serve the folder over `localhost` or deploy it over HTTPS. Service workers do not run from `file://` URLs.

## Connect live mandi prices

The app uses the official Open Government Data Platform's AGMARKNET daily market-price resource. This feed reports market, commodity, arrival date and minimum / maximum / modal wholesale prices, depending on the resource fields available.

1. Create an account on [data.gov.in](https://www.data.gov.in/) and request an API key from its API / profile area.
2. Open UdyamMitra → **Market Price Book** → **Live mandi prices**.
3. Paste your API key, keep the default resource ID or replace it with the ID shown on the official dataset, optionally filter by district / commodity, and click **Fetch latest prices**.
4. Check the returned market and arrival date before using a price. Government feeds may have delays or incomplete coverage.

Official dataset: https://www.data.gov.in/catalog/current-daily-price-various-commodities-various-markets-mandi
API reference / resource endpoint: https://api.data.gov.in/resource/9ef84268-d588-465a-a308-a864a43d0070

The API key is not saved by the app. In this prototype, the browser sends the key directly to data.gov.in. **Do not use that approach for a public production deployment**; create a server-side proxy and keep the API key in server environment variables. The browser may block direct API access because of CORS or the official service may temporarily be unavailable. In those cases the app displays an error and does not invent live values.

## Weather

The dashboard can fetch a 3-day forecast for selected Maharashtra towns from the Open-Meteo forecast API (temperature and precipitation probability / amount). Open-Meteo documents browser CORS support and no API key requirement for its free non-commercial endpoint; follow its attribution and usage terms: https://open-meteo.com/. Forecasts are not official severe-weather warnings. The app also links to the official India Meteorological Department website: https://mausam.imd.gov.in/ for warning verification.

## Prototype limitations — read before public use

- Registration / login and all business records are stored only in this browser on this device. They are **not** secure server-side accounts, and records do not sync between devices. Do not store sensitive customer or financial information in this demo.
- Do not treat the local demo login as production authentication. A production app needs server-side authentication, password hashing, access controls, backups and a database.
- The pricing and production planner uses formulas and user-entered data; it is not an AI forecast and cannot guarantee demand or profit.
- Distribution comparisons are estimates, not live buyer offers. The buyer directory is a private local notebook, not a searchable public marketplace.
- Sales receipts are simple records, not tax invoices.
- Weather forecasts can be fetched on demand from Open-Meteo for selected Maharashtra towns. Severe-weather warnings are not automatically fetched; the app links to official IMD warnings.
- Sample price-book entries are clearly marked as illustrative and are never presented as live API results.

## Sources

- Government of India OGD / AGMARKNET daily mandi prices: https://www.data.gov.in/catalog/current-daily-price-various-commodities-various-markets-mandi
- Open-Meteo Forecast API: https://open-meteo.com/en/docs
- India Meteorological Department: https://mausam.imd.gov.in/
