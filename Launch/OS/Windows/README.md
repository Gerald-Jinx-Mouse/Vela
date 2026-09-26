# Launch Vela on Windows 11

Vela is a web charting library, not a Windows desktop application. Run the included development playground to view and test the cloned repository in a browser.

## Requirements

- Windows 11
- PowerShell 7 or Windows PowerShell
- Node.js 22 LTS or newer, with npm
- An internet connection for the first dependency installation and live market data

Check whether Node.js and npm are available:

```powershell
node --version
npm --version
```

If either command is missing, install the current Node.js LTS release with Windows Package Manager:

```powershell
winget install --id OpenJS.NodeJS.LTS --exact
```

Close and reopen PowerShell after installation, then run the version checks again.

## First launch

Open PowerShell and run:

```powershell
Set-Location "C:\Projects\Vela"
npm install
npm run playground
```

Wait until Vite reports that the development server is ready. Then open:

<http://localhost:5190>

Keep the PowerShell window open while using Vela. The development server watches the source files and refreshes the playground as you make changes. Closing the browser tab does not stop the server. To exit, follow [Stop Vela](#stop-vela).

## Later launches

After the dependencies have been installed once, use:

```powershell
Set-Location "C:\Projects\Vela"
npm run playground
```

If `package.json` or `package-lock.json` changes after a pull, run `npm install` again before starting the playground.

## Stop Vela

The playground keeps running until you stop that PowerShell process. Return to the window where `npm run playground` is running and use either method:

- Press `q`, then Enter. Vite quits and returns you to the PowerShell prompt. Press `h`, then Enter, in that same window to list Vite's other shortcuts.
- Press `Ctrl+C`. If PowerShell asks whether to terminate the batch job, enter `Y` and press Enter.

## Troubleshooting

### PowerShell cannot find `node` or `npm`

Close every open PowerShell window and start a new one. If the commands are still unavailable, reinstall Node.js LTS with the command in the Requirements section.

### Port 5190 is already in use

Stop the other Vela/Vite process with `Ctrl+C`, or launch this copy on another port:

```powershell
npm run playground -- --port 5191
```

Then open <http://localhost:5191>.

### The page opens but live chart data does not load

The playground requests live data from public market-data providers. Confirm that Windows Firewall, a VPN, an ad blocker, or a corporate network is not blocking the browser or Node.js. No API key is required for the default Binance public-data example.

### Dependencies appear damaged or incomplete

Stop the server and reinstall exactly from the lock file:

```powershell
Set-Location "C:\Projects\Vela"
npm ci
npm run playground
```

## Optional project checks

These commands validate the project but are not required merely to open the playground:

```powershell
npm run typecheck
npm run lint
npm run test
npm run build
```
