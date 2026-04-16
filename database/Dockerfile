FROM postgres:17.2-alpine

# Les variables POSTGRES_DB, POSTGRES_USER et POSTGRES_PASSWORD
# sont injectées via le docker-compose.yml (fichier .env)
# Ne jamais hardcoder des credentials ici.

COPY sql/01-CreateScheme.sql /docker-entrypoint-initdb.d/
COPY sql/02-InsertData.sql /docker-entrypoint-initdb.d/
