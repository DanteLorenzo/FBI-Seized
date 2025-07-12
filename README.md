
# **FBI Seized Static Website**  

A simple static website served via Dockerized Nginx.  

## **Getting Started**  

### **Prerequisites**  
- Docker ([Install Docker](https://docs.docker.com/get-docker/))  
- Git (Optional)  

### **1. Clone the Repository**  
```bash
git clone https://github.com/DanteLorenzo/FBI-Seized.git
cd FBI-Seized
```

### **2. Run with Docker (Single Command)**  
#### **Option A: Using `docker run`**  
```bash
docker build -t fbi_seized . && \
docker run -p 80:80 -d --restart=unless-stopped --name fbi_website fbi_seized
```
- Access at: [http://localhost](http://localhost)  

#### **Option B: Using Docker Compose (Recommended)**  
1. **Edit `docker-compose.yml` (if needed)**  
   ```yaml
   version: '3.8'
   services:
     fbi_seized:
       container_name: fbi_website
       build: .
       ports:
         - "80:80"
       restart: unless-stopped
       networks:
         - master  # Optional (if using a custom network)
   
   networks:
     master:
       external: true  # Only if you have an existing 'master' network
   ```
2. **Start the container**  
   ```bash
   docker-compose up -d
   ```
   - Access at: [http://localhost](http://localhost)  

### **🛑 Stopping the Container**  
```bash
docker stop fbi_website && docker rm fbi_website
```
**or (if using Docker Compose)**  
```bash
docker-compose down
```

---

## **⚙️ Configuration**  
- **Custom Content**: Replace files in `src/` (they auto-sync with the container).  
- **Port Change**: Modify `ports` in `docker-compose.yml` (e.g., `8080:80`).  

---

## **📜 License**  
This project is for educational purposes only.  

---

### **Notes**  
- If you encounter permission issues, run:  
  ```bash
  chmod -R 755 src/
  ```
- For HTTPS, consider using a reverse proxy (e.g., Traefik, Nginx Proxy Manager).  

Let me know if you'd like further refinements! 🔧