### Web Scraper with MySQL (Dockerized)  

This project is a web scraper built using Python's `BeautifulSoup` to extract data from websites and store it in a MySQL database. The entire application is containerized using Docker, ensuring a scalable and portable deployment. The setup consists of two separate containers:  

- App Container: Runs the Python web scraping script, fetches data from websites, and sends it to the MySQL database.  
- MySQL Container: Hosts the database where the scraped data is stored.  

### Features:  
✅ Web scraping using `BeautifulSoup`  
✅ Stores extracted data in a structured MySQL database  
✅ Runs inside isolated Docker containers for scalability and portability  
✅ Establishes a direct connection between the App and MySQL containers  
✅ Does not require Docker Compose for container management  

### Technologies Used:  
- Python (`BeautifulSoup`, `MySQL Connector`)  
- MySQL (Relational Database Management System)  
- Docker (Containerization)  

### How to Run:  
### Step 1: Pull and Run the MySQL Container  
Run the following command to pull and start a MySQL container:  
```bash
docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=scraper_db -p 3306:3306 -d mysql:latest
```
- This command creates a MySQL container named `mysql-container`.  
- It sets the root password to `root` and creates a database named `scraper_db`.  
- MySQL is accessible on port `3306`.  

#### Step 2: Build and Run the App Container  
1. First, build the Docker image for the Python web scraper:  
   ```bash
   docker build -t web-scraper .
   ```
2. Run the container and link it to the MySQL container:  
   ```bash
   docker run --name scraper-app --link mysql-container -e DB_HOST=mysql-container -e DB_USER=root -e DB_PASSWORD=root -e       DB_NAME=scraper_db -d web-scraper
   ```
   - This connects the web scraper container to MySQL.  
   - Environment variables configure the database connection.  

#### Step 3: Verify Data Storage  
1. Connect to the MySQL container:  
   ```bash
   docker exec -it mysql-container mysql -uroot -proot
   ```
2. Check if the scraped data is stored:  
   ```sql
   USE scraper_db;
   SELECT * FROM your_table_name;
   ```

Now, the web scraper will extract data and store it in MySQL inside the containerized environment. 🚀
