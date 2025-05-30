# Sentry Self-Hosted – Startup and Shutdown Guide
Use `docker-compose` to bring up all services:
   docker-compose up -d

# 🛑 Shutdown Instructions

To safely shut down your Sentry instance:

 **Stop All Services:**
   docker-compose down

This stops and removes all containers but keeps volumes/data intact.


## 📝 Notes

- Default web port is `9000`
- Services like Redis, PostgreSQL, Kafka, Zookeeper, etc. are included and managed via Docker
- For production setups, consider enabling SSL and reverse proxying with NGINX or Traefik

- ## 📚 Documentation

[Sentry](https://sentry.io/), feature-complete and packaged up for low-volume deployments and proofs-of-concept.

Documentation [here](https://develop.sentry.dev/self-hosted/).
