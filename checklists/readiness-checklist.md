# Readiness Checklist â€“ LabÂ 05

ÄÃ¢y lÃ  danh sÃ¡ch kiá»ƒm tra (checklist) Ä‘á»ƒ Ä‘áº£m báº£o stack DockerÂ Compose cá»§a báº¡n Ä‘Ã£ sáºµn sÃ ng trÆ°á»›c khi gá»­i bÃ i. HÃ£y tick vÃ o má»—i má»¥c sau khi hoÃ n thÃ nh.

- [x] **Database ready:** container DB Ä‘Ã£ cháº¡y vÃ  pháº£n há»“i `pg_isready`. Kiá»ƒm tra báº±ng `docker exec -it fit4110-db-lab05 pg_isready -U $POSTGRES_USER`.
- [x] **AI service ready:** container AI service tráº£ vá» `200` cho endpoint `/health` vÃ  `/predict` hoáº¡t Ä‘á»™ng.
- [x] **API ready:** container API tráº£ `200` cho `/health` vÃ  cÃ³ thá»ƒ táº¡o/láº¥y readings khi token há»£p lá»‡.
- [x] **Environment variables:** `.env` Ä‘Ã£ Ä‘Æ°á»£c thiáº¿t láº­p Ä‘Ãºng (APP_PORT, POSTGRES_USER, AUTH_TOKEN,â€¦). KhÃ´ng sá»­ dá»¥ng secret tháº­t; lÆ°u secret vÃ o `.env` cá»¥c bá»™, commit `.env.example`.
- [x] **Network & Ports:** máº¡ng `team-internal` hoáº¡t Ä‘á»™ng; API gá»i Ä‘Æ°á»£c AI báº±ng hostname `ai-service`; ports 8000 (API), 9000 (AI) vÃ  5432 (DB) Ä‘Æ°á»£c map Ä‘Ãºng.
- [x] **Image tags:** báº¡n Ä‘Ã£ build image vá»›i tag `v0.1.0-<team>` vÃ  push lÃªn registry (ghcr.io hoáº·c DockerÂ Hub). XÃ¡c nháº­n ráº±ng tag xuáº¥t hiá»‡n trong registry.

Ghi chÃº thÃªm nhá»¯ng váº¥n Ä‘á» gáº·p pháº£i hoáº·c Ä‘iá»u chá»‰nh táº¡i Ä‘Ã¢y:

```
- MÃ´ táº£â€¦
```
