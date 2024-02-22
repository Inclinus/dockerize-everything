# Créer un Dockerfile pour cette application en mode production
# 1. Utiliser une image de base
FROM rustlang/rust:nightly

# 2. Définir le répertoire de travail
WORKDIR /blog

# 3. Installer les paquets système nécessaires
RUN apt-get update && apt-get install -y libpq-dev

# 7. Installer la CLI Diesel
RUN cargo install diesel_cli --no-default-features --features postgres

# 5. Copier les fichiers de l'application
# COPY migrations migrations
# COPY templates templates
# COPY static static
# COPY src src
# COPY Cargo.toml Cargo.toml
# COPY Cargo.lock Cargo.lock
# COPY diesel.toml diesel.toml
# COPY .env .env

COPY . .

# 6. Compiler l'application
RUN cargo install --path . && \
    cp /usr/local/cargo/bin/blog ./blog


# plutot health check sur le service db que le sleep
CMD ["sh", "-c", "sleep 10 && diesel migration run && ./blog"]
