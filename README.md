# Dockerized Web Scraper with MySQL Integration using Python

This project demonstrates how to build a **Dockerized web scraper** using Python that scrapes movie quotes from a website and stores the data in a **MySQL database** running in a separate Docker container. The setup uses a **custom Docker network** with the `bridge` driver for container communication.

## 🚀 Features:
- **Web Scraping** with Python using the `requests` and `BeautifulSoup` libraries.
- **Dockerized MySQL** container to store the scraped data.
- Custom **Docker network** setup (`--driver bridge --subnet 172.18.0.0/16`).
- No **Docker Compose** used — everything set up with individual Docker commands.

## 🛠️ Prerequisites:
- Docker installed on your machine.
- Basic understanding of Docker and Python.
- Python packages: `requests`, `BeautifulSoup`, `mysql-connector-python`.

