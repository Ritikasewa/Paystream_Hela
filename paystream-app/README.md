# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) (or [oxc](https://oxc.rs) when used in [rolldown-vite](https://vite.dev/guide/rolldown)) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## React Compiler

The React Compiler is not enabled on this template because of its impact on dev & build performances. To add it, see [this documentation](https://react.dev/learn/react-compiler/installation).

## Expanding the ESLint configuration

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and [`typescript-eslint`](https://typescript-eslint.io) in your project.

## Connect to a contract deployed in Remix

This app reads the smart contract address from `VITE_CONTRACT_ADDRESS` (falls back to the hardcoded address in `src/contractInfo.js`).

1) Deploy in Remix
- Open Remix → **Deploy & Run Transactions**
- Environment: **Injected Provider - MetaMask**
- Make sure MetaMask is on **HeLa Testnet** (chain id `666888`)
- Deploy your contract

2) Copy the deployed address
- In Remix, copy the deployed contract address (e.g. `0xabc...`)

3) Point `paystream-app` at it
- Create `paystream-app/.env.local`:
	- `VITE_CONTRACT_ADDRESS=0xYOUR_DEPLOYED_ADDRESS`
- Restart the dev server if it’s running.

Notes:
- If you changed the contract interface in Remix, you must also update `CONTRACT_ABI` in `src/contractInfo.js` to match the compiled ABI.

## Run all 3 services (backend + both frontends)

Ports used:
- Backend: `http://localhost:5050`
- Employee app (this Vite app): `http://localhost:5173`
- HR dashboard (CRA): `http://localhost:3000`

1) Start the backend
- `cd "../project/backend"`
- `npm install`
- `npm start`
- Check: open `http://localhost:5050/health`

2) Start the employee app (paystream-app)
- `cd "../../paystream-app"`
- `npm install`
- `npm run dev`

3) Start the HR dashboard
- `cd "../paystream-hr-dashboard"`
- `npm install`
- `npm start`

Environment variables:
- `paystream-app/.env.local`
	- `VITE_CONTRACT_ADDRESS=0x...`
	- `VITE_BACKEND_URL=http://localhost:5050`
- `paystream-hr-dashboard/.env.local`
	- `REACT_APP_BACKEND_URL=http://localhost:5050`
