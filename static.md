🎯 Aim

To deploy a static website using Docker by containerizing an NGINX web server.

⚙️ Requirements
Docker installed
Basic HTML files
Terminal / Command line access
📘 Theory

Docker is a containerization platform that packages an application and its dependencies into a lightweight container. A static website can be hosted using an NGINX container by mounting HTML files into the container.

📁 Project Structure
static-website/
│── index.html
│── Dockerfile
🧾 1. index.html
<!DOCTYPE html>
<html>
<head>
    <title>My Static Website</title>
</head>
<body>
    <h1>Hello from Docker Static Website 🚀</h1>
    <p>Deployed using NGINX container</p>
</body>
</html>
🧾 2. Dockerfile
FROM nginx:alpine

# Remove default nginx website
RUN rm -rf /usr/share/nginx/html/*

# Copy our website files
COPY . /usr/share/nginx/html

# Expose port 80
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
🚀 Steps to Deploy
1. Build Docker Image
docker build -t static-website .
2. Run Docker Container
docker run -d -p 8080:80 static-website
3. Open in Browser
http://localhost:8080
📌 Output

You will see:

Hello from Docker Static Website 🚀
Deployed using NGINX container
🧾 Result

A static website was successfully deployed using Docker container with NGINX web server.

📘 Conclusion

Docker simplifies deployment by packaging web applications into portable containers that can run consistently across any environment.