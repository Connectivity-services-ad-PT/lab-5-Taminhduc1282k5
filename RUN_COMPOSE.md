# RUN_COMPOSE.md â€“ HÆ°á»›ng dáº«n cháº¡y LabÂ 05

TÃ i liá»‡u nÃ y hÆ°á»›ng dáº«n ngÆ°á»i khÃ¡c clone repo sáº¡ch vÃ  cháº¡y láº¡i stack Compose cá»§a LabÂ 05.

---

##Â 1.Â Clone repo

```bash
git clone <repo-url>
cd FIT4110_lab05_docker_compose_readiness
```

---

##Â 2.Â CÃ i dependencies cho Newman/Prism/Spectral (tuá»³ chá»n)

```bash
npm install
```

---

##Â 3.Â Build & cháº¡y stack DockerÂ Compose

```bash
# Copy .env.example sang .env vÃ  chá»‰nh sá»­a náº¿u cáº§n
cp .env.example .env

# Build images (náº¿u chÆ°a cÃ³) vÃ  khá»Ÿi Ä‘á»™ng cÃ¡c container trong ná»n
docker network create class-net 2>/dev/null || true
docker compose up -d --build
```

Lá»‡nh trÃªn sáº½ táº¡o cÃ¡c container:

- `fit4110-db-lab05` (PostgreSQL)
- `fit4110-ai-lab05` (AI service máº«u cháº¡y portÂ 9000)
- `fit4110-api-lab05` (API FastAPI trÃªn portÂ 8000)

Theo dÃµi log:

```bash
docker compose logs -f
```

Sau vÃ i giÃ¢y, kiá»ƒm tra health cá»§a má»—i service:

```bash
# API
curl http://localhost:8000/health

# AI service
curl http://localhost:9000/health

# DB readiness
docker exec -it fit4110-db-lab05 pg_isready -U $POSTGRES_USER
```

Báº¡n cÅ©ng cÃ³ thá»ƒ truy cáº­p endpoint `/predict` cá»§a AI service Ä‘á»ƒ xem káº¿t quáº£ máº«u:

```bash
curl -X POST http://localhost:9000/predict
```

---

##Â 4.Â Cháº¡y Newman test trÃªn stack Compose (tuá»³ chá»n)

```bash
npm run test:compose
```

Report sinh táº¡i:

```text
reports/newman-lab05-compose.xml
reports/newman-lab05-compose.html
```

---

##Â 5.Â Dá»«ng stack

Khi khÃ´ng cáº§n ná»¯a, dá»«ng vÃ  xoÃ¡ cÃ¡c container báº±ng:

```bash
docker compose down
```

Náº¿u muá»‘n xoÃ¡ volume dá»¯ liá»‡u cá»§a DB, thÃªm tuá»³ chá»n `-v`:

```bash
docker compose down -v
```

---

##Â 6.Â Lá»‡nh nhanh

Báº¡n cÃ³ thá»ƒ dÃ¹ng Makefile:

```bash
make compose-up
make compose-down
make logs
```

---

##Â 7.Â Máº¹o gá»¡ lá»—i

- Sá»­ dá»¥ng `docker compose ps` Ä‘á»ƒ xem tráº¡ng thÃ¡i container.
- Náº¿u API tráº£ lá»—i káº¿t ná»‘i DB, hÃ£y kiá»ƒm tra biáº¿n mÃ´i trÆ°á»ng `POSTGRES_*` trong `.env` vÃ  Ä‘áº£m báº£o DB Ä‘Ã£ sáºµn sÃ ng (`pg_isready`).
- Náº¿u AI service cáº§n táº£i mÃ´ hÃ¬nh lá»›n, tÄƒng `start_period` cá»§a healthcheck trong `docker-compose.yml`.

