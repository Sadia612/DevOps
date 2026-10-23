# Lab 4: Simple Python Database Connections

**Student:** sadia612 (`sadia612@ubuntu`)
**Databases fork:** https://github.com/Sadia612/Databases
**Written answers:** [Lab4_Solution.pdf](Lab4_Solution.pdf)

One Python file, `db_connect.py`, is edited through four stages. Docker runs the databases; Python runs directly on Ubuntu.

| Stage | Database | Settings come from |
|---|---|---|
| Task 4 | MySQL | Code |
| Task 5 | MongoDB | Code |
| Task 6 | MongoDB | Environment variables (`os.getenv()`) |
| Task 7 | MongoDB | `credentials.ini` (`configparser`) |

## Endpoints

| Database | Endpoint | Name |
|---|---|---|
| MySQL | `127.0.0.1:3307` | `school_mysql` |
| MongoDB dev | `127.0.0.1:27017` | `school_dev` |
| MongoDB test | `127.0.0.1:27018` | `school_test` |
| MongoDB prod (simulated) | `127.0.0.1:27019` | `school_prod` |

## Run

```bash
cd ~/Databases
source .venv/bin/activate
docker compose up -d --wait mysql mongo-dev mongo-test mongo-prod
export APP_ENV=dev        # or test, or prod
python db_connect.py
```

Expected output (each run prints the database name, port and its stored environment):

```
Connected to MongoDB: school_prod
Server: ('127.0.0.1', 27019)
Environment: prod
```

## Notes

- **Kernel fix:** MongoDB 8.0 crashes on Linux kernel 6.19+ (SERVER-121912). I added `compose.override.yaml` setting `GLIBC_TUNABLES=glibc.pthread.rseq=1` for the three Mongo services. The supplied `compose.yaml` is unchanged.
- **Low memory:** MySQL was stopped once (exit 137) on a 1.6 GB server; `docker compose up -d --wait mysql` restarted it.
- **Security:** `credentials.ini` is plaintext, set to `chmod 600` and ignored by Git. No passwords appear in this README.

## Evidence

All 15 required screenshots and the 3 exam screenshots (`Q1`, `Q2`, `Q3`) are in `screenshots/`.

## Cleanup

```bash
docker compose down
```
