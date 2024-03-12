# Static FBI Website Seized 

## Getting Started

Clone the repository:

```
git clone https://github.com/DanteLorenzo/FBI-Seized.git
```
```
cd FBI-Seized
```

Build Docker image and run it:

```
docker build -t fbi_seized .
```
```
docker run -p 80:80 -d --restart=unless-stopped fbi_seized
```

---