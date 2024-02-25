# Créer un Dockerfile pour cette application en mode production
# 1. Utiliser une image de base
FROM rustlang/rust:nightly

WORKDIR /blog

RUN apt-get update && apt-get install -y libpq-dev

RUN cargo install diesel_cli --no-default-features --features postgres

COPY . .

RUN cargo install --path . && \
    cp /usr/local/cargo/bin/blog ./blog

CMD ["diesel", "migration", "run"]

CMD ["./blog"]
