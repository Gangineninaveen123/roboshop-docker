# RoboShop – Dockerized Microservices

A multi-container e-commerce application (RoboShop) run with Docker Compose. Each service has its own Dockerfile.

## Services
| Service | Folder |
|---|---|
| Frontend | `frontend` |
| Catalogue | `catalogue` |
| User | `user` |
| Cart | `cart` |
| Shipping | `shipping` |
| Payment | `payment` |
| MongoDB | `mongodb` |
| MySQL | `mysql` |

## What's inside
- A Dockerfile for each service
- `docker-compose.yaml` to run all the containers together on a custom bridge network

## Tech
Docker, Docker Compose, MongoDB, MySQL

## How to run
```bash
git clone https://github.com/Gangineninaveen123/roboshop-docker.git
cd roboshop-docker
docker compose up -d
```

To stop everything:
```bash
docker compose down
```
