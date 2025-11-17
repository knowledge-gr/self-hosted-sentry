# Sentry Self-Hosted – Startup and Shutdown Guide
Use `docker-compose` to bring up all services:
  `docker-compose up -d`
Safe option : 
`docker compose up --wait`
  

# 🛑 Shutdown Instructions

To safely shut down your Sentry instance:

 **Stop All Services:**
   `docker-compose down`

This stops and removes all containers but keeps volumes/data intact.


## 📝 Notes

- Default web port is `9000`
- Services like Redis, PostgreSQL, Kafka, Zookeeper, NGINX etc. are included and managed via Docker

- ## 📚 Documentation

[Sentry](https://sentry.io/), feature-complete and packaged up for low-volume deployments and proofs-of-concept.

Documentation [here](https://develop.sentry.dev/self-hosted/).

Για Rentetion manualy 

https://develop.sentry.dev/self-hosted/troubleshooting/postgres/ 

Δουλεψε ο τροπος με το delete και VACUM

Πρώτα με το tool που είναι στο Sentry 

docker exec -it sentry-self-hosted-web-1 sentry cleanup --days 90

Αν δεν πάμε στα από κάτω

docker compose run --rm -T web cleanup --days 7 -m nodestore -l debug

docker exec -it pg_container bash

psql -h postgres -U postgres -d postgres

DELETE FROM public.nodestore_node WHERE "timestamp" < NOW() - INTERVAL '[SENTRY_RETENTION_DAYS] DAY';
VACUUM FULL public.nodestore_node;

Αν δεν παίξει με την μια το vacuum λόγω του storage

REINDEX TABLE public.nodestore_node;
