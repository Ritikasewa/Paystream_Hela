# PayStream Backend (Express)

## Run

- `npm install`
- `npm start`

Default dev URL:
- `http://localhost:5050`

Health check:
- `GET /health`

Frontend endpoints:
- `GET /api/stats`
- `GET /api/compliance`

## Notes

- Port is controlled by `PORT` in `.env` (set to `5050` by default).
- CORS is currently configured as `origin: "*"` for local development.
