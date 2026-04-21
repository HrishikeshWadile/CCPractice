Prerequisites (Free)
Google account
Install Google Cloud SDK
🔧 Step 1: Install Google Cloud SDK

Download from:
https://cloud.google.com/sdk/docs/install

After install:

gcloud init

Login and select/create project.

🏗️ Step 2: Create App Engine Project
gcloud app create
Select region (e.g., asia-south1)
🐍 Option A: Python Hello World App
📁 Project Structure
app.yaml
main.py
requirements.txt
📝 main.py
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return "Hello, Google App Engine!"

if __name__ == '__main__':
    app.run(host='127.0.0.1', port=8080, debug=True)
📝 requirements.txt
flask
📝 app.yaml
runtime: python39
▶️ Run Locally
python main.py

Open:

http://localhost:8080
☁️ Deploy to App Engine
gcloud app deploy
🌐 Open App
gcloud app browse
☕ Option B: Java Hello World (Servlet)
📁 Structure (Maven)
pom.xml
src/main/java/HelloServlet.java
src/main/webapp/WEB-INF/web.xml
app.yaml
📝 HelloServlet.java
import java.io.IOException;
import javax.servlet.*;
import javax.servlet.http.*;

public class HelloServlet extends HttpServlet {
    public void doGet(HttpServletRequest req, HttpServletResponse resp)
        throws IOException {
        resp.setContentType("text/plain");
        resp.getWriter().println("Hello, Google App Engine!");
    }
}
📝 web.xml
<web-app>
  <servlet>
    <servlet-name>hello</servlet-name>
    <servlet-class>HelloServlet</servlet-class>
  </servlet>
  <servlet-mapping>
    <servlet-name>hello</servlet-name>
    <url-pattern>/</url-pattern>
  </servlet-mapping>
</web-app>
📝 app.yaml
runtime: java11
▶️ Deploy
gcloud app deploy
🎯 What to Perform in Exam
Show project files
Run locally
Deploy using gcloud app deploy
Open live URL
🎤 Viva Answers

Q: What is Google App Engine?
→ A Platform-as-a-Service (PaaS) to deploy web apps without managing servers

Q: Which cloud model?
→ PaaS

Q: Advantage?
→ Auto scaling, no server management

Q: Languages supported?
→ Python, Java, Node.js, Go, etc.

💡 Extra (for better marks)

Modify app:

@app.route('/name/<user>')
def greet(user):
    return f"Hello {user}!"