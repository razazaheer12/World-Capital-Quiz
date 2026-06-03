## TODO - Deploy World-Capital-Quiz to Vercel

- [x] Update `index.js` to:
  - use `process.env.PORT` (Vercel requirement)
  - use Vercel Postgres connection env vars (no hardcoded localhost credentials)
  - avoid `db.end()` pattern that breaks initial data loading

- [x] Verify app boot locally (optional): `npm install` then `node index.js`

- [ ] Push changes to GitHub branch
- [ ] In Vercel project:
  - set environment variables for Postgres connection
  - set correct build/start commands if required
- [ ] Deploy and confirm the homepage loads and quiz works

